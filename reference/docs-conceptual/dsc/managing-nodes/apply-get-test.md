---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 在節點上套用、取得並測試設定
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953835"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a>在節點上套用、取得並測試設定

本指南將示範如何在目標節點上使用設定。 本指南會分成下列步驟：

## <a name="apply-a-configuration"></a>套用設定

為了套用和管理設定，我們需要產生一個 ".mof" 檔案。 下列程式碼表示將在這整份指南中使用的簡單設定。

```powershell
Configuration Sample
{
    # This will generate two .mof files, a localhost.mof, and a server02.mof
    Node localhost, server02
    {
        File SampleFile
        {
            DestinationPath = 'C:\Temp\temp.txt'
            Contents = 'This is a simple resource to show Configuration functionality on a Node.'
        }
    }
}

# The -OutputPath parameter is built into every Configuration automatically.
# The value of -OutputPath determines where the .mof file should be stored, once compiled.
Sample -OutputPath "C:\Temp\"
```

編譯此設定將產生兩個 ".mof" 檔案。

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

若要套用設定，請使用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet。 `-Path` 參數會指定 ".mof" 檔案所在的目錄。 若未指定 `-Computername`，`Start-DSCConfiguration` 會嘗試將每個設定套用至 '.mof' 檔案名稱 (\<computername\>.mof) 所指定的電腦名稱。 為 `Start-DSCConfiguration` 指定 `-Verbose` 以查看更詳盡的輸出。

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

若未指定 `-Wait`，您就會看到建立了一個作業。 針對 `Start-DSCConfiguration` 所處理的每個 ".mof" 檔案，所建立的作業將會有一個 **ChildJob**。

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

如果設定花費了很長的時間，而您想要停止它，您可以使用 [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) 來停止本機節點上的應用程式。

```powershell
Stop-DSCConfiguration -Force
```

完成之後，您就能透過 [Get-Job](/powershell/module/microsoft.powershell.core/get-job) 所傳回的作業物件來檢視作業的狀態。

```powershell
$job = Get-Job
$job.ChildJobs
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

若要查看 **Verbose** 輸出，使用下列命令來檢視每個 **ChildJob** 的 **Verbose** 資料流。 如需 PowerShell 作業的詳細資訊，請參閱 [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)。

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-124525095-708259637-1543119021-1282804.
[SERVER01]: LCM:  [ Start  Set      ]
[SERVER01]: LCM:  [ Start  Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ Start  Test     ]  [[File]SampleFile]
[SERVER01]:                            [[File]SampleFile] The destination object was found and no action is required.
[SERVER01]: LCM:  [ End    Test     ]  [[File]SampleFile]  in 0.0370 seconds.
[SERVER01]: LCM:  [ Skip   Set      ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Set      ]
[SERVER01]: LCM:  [ End    Set      ]    in  0.2400 seconds.
Operation 'Invoke CimMethod' complete.
```

從 PowerShell 5.0 開始，已在 `Start-DSCConfiguration` 中新增 `-UseExisting` 參數。 藉由指定 `-UseExisting`，您可以指示 Cmdlet 使用目前套用的設定，而不是 `-Path` 參數所指定的設定。

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a>測試設定

您可以使用 [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) 來測試目前套用的設定。 如果節點符合規範，`Test-DSCConfiguration` 將傳回 `True`，如果不符合，則會傳回 `False`。

```powershell
Test-DSCConfiguration
```

從 PowerShell 5.0 開始，已新增 `-Detailed` 參數，它會傳回一個物件，其中含有適用於 **ResourcesInDesiredState** 和 **ResourcesNotInDesiredState** 的集合

```powershell
Test-DSCConfiguration -Detailed
```

從 PowerShell 5.0 開始，您可以在不套用設定的情況下測試設定。 `-ReferenceConfiguration` 參數會接受 ".mof" 檔案的路徑，據以測試節點。 不需針對節點採取任何**設定**動作。 PowerShell 4.0 中提供可在不套用設定的情況下測試設定的因應措施，但不會在此討論它們。

## <a name="get-configuration-values"></a>取得設定值

[Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) Cmdlet 會傳回目前套用的設定中任何已設定資源的目前值。

```powershell
Get-DSCConfiguration
```

如果成功套用，則我們範例設定的輸出看起來像這樣。

```output
ConfigurationName    : Sample
DependsOn            :
ModuleName           : PSDesiredStateConfiguration
ModuleVersion        :
PsDscRunAsCredential :
ResourceId           : [File]SampleFile
SourceInfo           :
Attributes           : {archive}
Checksum             :
Contents             :
CreatedDate          : 11/27/2018 7:16:06 AM
Credential           :
DestinationPath      : C:\Temp\temp.txt
Ensure               : present
Force                :
MatchSource          :
ModifiedDate         : 11/27/2018 7:16:06 AM
Recurse              :
Size                 : 75
SourcePath           :
SubItems             :
Type                 : file
PSComputerName       :
CimClassName         : MSFT_FileDirectoryConfiguration
```

## <a name="get-configuration-status"></a>取得設定狀態

從 PowerShell 5.0 開始，[Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) Cmdlet 可讓您查看將設定套用至節點的記錄。 PowerShell DSC 會持續追蹤在**推送**或**提取**模式中最後套用的 {{N}} 個設定。 這包括 LCM 所執行的任何「一致性」  檢查。 根據預設，`Get-DSCConfigurationStatus` 只會顯示最後一個記錄項目。

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

使用 `-All` 參數來查看所有設定狀態記錄。

> [!NOTE]
> 為求簡單明瞭，會截斷輸出。

```powershell
Get-DSCConfigurationStatus -All
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
Success    11/27/2018 7:16:06 AM     Initial         PUSH  False                1
Success    11/27/2018 7:04:53 AM     Initial         PUSH  False                1
Success    11/27/2018 7:03:45 AM     Consistency     PUSH  False                2
Success    11/27/2018 7:03:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:48:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:44 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:18:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:03:44 AM     Consistency     PUSH  False                2
```

## <a name="manage-configuration-documents"></a>管理設定文件

LCM 會使用**設定文件**來管理節點的設定。 這些 ".mof" 檔案均位於 "C:\Windows\System32\Configuration" 目錄。

從 PowerShell 5.0 開始，[Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) 可讓您移除 ".mof" 檔案，以停止未來的一致性檢查，或移除套用時發生錯誤的設定。 `-Stage` 參數可讓您指定要移除哪一個 ".mof" 檔案。

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> 在 PowerShell 4.0 中，您仍然可以直接使用 [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) 來移除這些 ".mof" 檔案。

## <a name="publish-configurations"></a>發佈設定

從 PowerShell 5.0 開始，已新增 [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) Cmdlet。 此 Cmdlet 可讓您將 ".mof" 檔案發佈至遠端電腦，而不需套用它。

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a>另請參閱

- [取得、測試及設定](../resources/get-test-set.md)
