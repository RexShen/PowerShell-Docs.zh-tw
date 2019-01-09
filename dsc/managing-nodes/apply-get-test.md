---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 在節點上套用、取得並測試設定
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400855"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a>在節點上套用、取得並測試設定

本指南將示範如何使用組態在目標節點上。 本指南會分成下列步驟：

## <a name="apply-a-configuration"></a>套用組態

若要套用管理設定，我們要產生 「.mof 」 檔案。 下列程式碼將代表簡單的設定將用於本指南。

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

編譯此組態會產生兩個 「.mof 」 檔案。

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

若要套用設定，請使用[Start-dscconfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet。 `-Path`參數指定".mof 」 檔案所在的目錄。 如果沒有`-Computername`指定，則`Start-DSCConfiguration`會嘗試將每個組態套用至 '.mof' 檔案的名稱所指定電腦名稱 (\<computername\>.mof)。 指定`-Verbose`至`Start-DSCConfiguration`以查看更詳細的輸出。

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

如果`-Wait`未指定，您會看到建立的一項作業。 建立的作業會有一個**ChildJob**每個 「.mof"檔案處理`Start-DSCConfiguration`。

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

如果設定花費很長的時間，而且您想要將它停止，您可以使用[Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)本機節點上停止應用程式。

```powershell
Stop-DSCConfiguration -Force
```

完成後，您可以檢視所傳回的工作物件透過作業的狀態[Get-job](/powershell/module/microsoft.powershell.core/get-job)。

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

若要查看**Verbose**輸出，使用下列命令來檢視**Verbose**每個資料流**ChildJob**。 如需有關 PowerShell 工作的詳細資訊，請參閱[about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)。

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

從 PowerShell 5.0`-UseExisting`參數已加入至`Start-DSCConfiguration`。 藉由指定`-UseExisting`，您可以指示 cmdlet 來使用現有套用的設定，而不是一個由`-Path`參數。

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a>測試組態

您可以測試目前套用的設定使用[Test-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)。 `Test-DSCConfiguration` 會傳回`True`如果節點是符合規範，與`False`如果不是。

```powershell
Test-DSCConfiguration
```

從 PowerShell 5.0`-Detailed`已新增參數，它會傳回集合的物件**ResourcesInDesiredState**和**ResourcesNotInDesiredState**

```powershell
Test-DSCConfiguration -Detailed
```

在 PowerShell 5.0 開始，可以測試組態而不套用它。 `-ReferenceConfiguration`參數可接受的 「.mof"檔案來測試依據的節點路徑。 否**設定**動作都會針對該節點。 在 PowerShell 4.0 中，有因應措施若要測試組態，而不套用它，但不是會在此討論。

## <a name="get-configuration-values"></a>取得組態值

[Get-dscconfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet 會傳回在目前套用的設定中設定的任何資源的目前值。

```powershell
Get-DSCConfiguration
```

如果已成功套用，從我們的範例組態的輸出會看起來像這樣。

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

從 PowerShell 5.0 [Get-dscconfigurationstatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet 可讓您查看的節點套用組態的歷程記錄。 PowerShell DSC 記錄的最後的 {{N}} 設定中套用**推播**或是**提取**模式。 這包括任何*一致性*LCM 所執行的檢查。 根據預設，`Get-DSCConfigurationStatus`之最後一個記錄項目只會顯示您。

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

使用`-All`參數，以查看所有的組態狀態歷程記錄。

> [!NOTE]
> 為求簡單明瞭，便會截斷輸出。

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

LCM 使用來管理節點的組態**設定文件**。 這些 「.mof"檔案位於 「 C:\Windows\System32\Configuration"的目錄中。

從 PowerShell 5.0 [Remove-dscconfigurationdocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)可讓您移除 「.mof"檔案來停止未來的一致性檢查，或移除發生錯誤時套用的設定。 `-Stage`參數可讓您指定您想要移除哪一個 「.mof 」 檔案。

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> 在 PowerShell 4.0 中，您仍然可以移除直接使用這些 「.mof"檔案[Remove-item](/powershell/module/microsoft.powershell.management/remove-item)。

## <a name="publish-configurations"></a>發行設定

從 PowerShell 5.0 [Publish-dscconfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet 已新增。 此 cmdlet 可讓您發佈至遠端電腦的".mof 」 檔案，而不套用它。

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a>另請參閱

- [取得、測試及設定](../resources/get-test-set.md)
