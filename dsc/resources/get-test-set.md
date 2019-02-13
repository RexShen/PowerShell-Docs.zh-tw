---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: Get-Test-Set
ms.openlocfilehash: 6d059518a49926bc5fb56e37e7d3d4d2c66bddec
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679001"
---
# <a name="get-test-set"></a>Get-Test-Set

>適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

![取得、測試及設定](/media/get-test-set.png)

會建構 PowerShell Desired State Configuration**取得**，**測試**，並**設定**程序。 DSC[資源](resources.md)每個包含的方法可以完成上述各項作業。 在 [組態](../configurations/configurations.md)，您定義填滿成為資源參數的索引鍵中的資源區塊**取得**，**測試**，和**設定**方法。

這是語法**服務**資源區塊。 **服務**資源會設定 Windows 服務。

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

**取得**，**測試**，並**設定**方法**服務**資源會有接受這些值的參數區塊。

```powershell
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [System.String]
        $Name,

        [System.String]
        [ValidateSet("Automatic", "Manual", "Disabled")]
        $StartupType,

        [System.String]
        [ValidateSet("LocalSystem", "LocalService", "NetworkService")]
        $BuiltInAccount,

        [System.Management.Automation.PSCredential]
        [ValidateNotNull()]
        $Credential,

        [System.String]
        [ValidateSet("Running", "Stopped")]
        $State="Running",

        [System.String]
        [ValidateNotNullOrEmpty()]
        $DisplayName,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Description,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Path,

        [System.String[]]
        [ValidateNotNullOrEmpty()]
        $Dependencies,

        [System.String]
        [ValidateSet("Present", "Absent")]
        $Ensure="Present"
    )
```

> [!NOTE]
> 語言和用來定義資源的方法會決定如何**取得**，**測試**，並**設定**會定義方法。

因為**服務**資源只有一個必要的索引鍵 (`Name`)，則**服務**區塊資源可能是這麼簡單：

```powershell
Configuration TestConfig
{
    Import-DSCResource -Name Service
    Node localhost
    {
        Service "MyService"
        {
            Name = "Spooler"
        }
    }
}
```

當您編譯上述的組態時，就會產生 「.mof 」 檔案中儲存您指定的索引鍵的值。 如需詳細資訊，請參閱 < [MOF](/windows/desktop/wmisdk/managed-object-format--mof-)。

```
instance of MSFT_ServiceResource as $MSFT_ServiceResource1ref
{
SourceInfo = "::5::1::Service";
 ModuleName = "PsDesiredStateConfiguration";
 ResourceID = "[Service]MyService";
 Name = "Spooler";

ModuleVersion = "1.0";

 ConfigurationName = "Test";

};
```

套用時，[本機設定管理員](../managing-nodes/metaConfig.md)將 「 多工緩衝處理器 」 的值從".mof"檔案讀取，並將它傳遞給`-Name`參數**取得**，**測試**，並**設定**"MyService"執行個體的方法**服務**資源。

## <a name="get"></a>取得

**取得**方法的資源，擷取資源的狀態，因為它在目標節點上進行設定。 此狀態會當成[雜湊表](/powershell/module/microsoft.powershell.core/about/about_hash_tables)。 索引鍵**雜湊表**會是可設定的值或參數，資源會接受。

**取得**方法會直接對應至[Get-dscconfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet。 當您呼叫`Get-DSCConfiguration`，在 LCM 執行**取得**目前套用的設定中每個資源的方法。 LCM 會使用儲存在 「.mof"檔案做為參數，每個對應的資源執行個體的索引鍵值。

這是範例輸出**服務**設定 「 多工緩衝處理器 」 服務的資源。

```output
ConfigurationName    : Test
DependsOn            :
ModuleName           : PsDesiredStateConfiguration
ModuleVersion        : 1.1
PsDscRunAsCredential :
ResourceId           : [Service]Spooler
SourceInfo           :
BuiltInAccount       : LocalSystem
Credential           :
Dependencies         : {RPCSS, http}
Description          : This service spools print jobs and handles interaction with the printer.  If you turn off
                       this service, you won’t be able to print or see your printers.
DisplayName          : Print Spooler
Ensure               :
Name                 : Spooler
Path                 : C:\WINDOWS\System32\spoolsv.exe
StartupType          : Automatic
State                : Running
Status               :
PSComputerName       :
CimClassName         : MSFT_ServiceResource
```

輸出會顯示目前的值屬性可由設定**服務**資源。

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

## <a name="test"></a>Test

**測試**資源的方法會判斷目標節點是否與資源的目前相容*期望狀態*。 **測試**方法會傳回`$True`或`$False`只以指出節點是否符合規範。
當您呼叫[Test-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)，，LCM 會呼叫**測試**目前套用的設定中每個資源的方法。 LCM 會使用儲存在 「.mof"檔案做為參數，每個對應的資源執行個體的索引鍵值。

如果結果的任何個別的資源**測試**是`$False`，`Test-DSCConfiguration`傳回`$False`指出的節點不符合規範。 如果所有的資源**測試**方法會傳回`$True`，`Test-DSCConfiguration`傳回`$True`表示節點為符合規範。

```powershell
Test-DSCConfiguration
```

```output
True
```

在 PowerShell 5.0 中，從開始`-Detailed`參數已加入。 指定`-Detailed`會導致`Test-DSCConfiguration`傳回物件，其中包含集合的結果符合規範且不符合規範的資源。

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

如需詳細資訊，請參閱[Test-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)

## <a name="set"></a>設定

**設定**資源的方法會嘗試強制的節點，以符合規範的資源時*期望狀態*。 **設定**方法僅供**具有等冪性**，這表示**設定**會多次執行，且一律取得相同的結果正確無誤。  當您執行[Start-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration)、 LCM 循環，透過目前套用的設定中每個資源。 LCM".mof 」 檔案中擷取目前的資源執行個體的索引鍵值，並使用它們做為參數**測試**方法。 如果**測試**方法會傳回`$True`，該節點是符合目前的資源，而**設定**方法會略過。 如果**測試**傳回`$False`，節點是不符合規範。  LCM 資源執行個體的索引鍵會將值傳遞做為參數的資源**設定**節點還原為合規性的方法。

藉由指定`-Verbose`並`-Wait`參數，您可以觀看的進度`Start-DSCConfiguration`cmdlet。 在此範例中，節點是已經符合規範。 `Verbose`輸出指出**設定**方法已略過。

```
PS> Start-DSCConfiguration -Verbose -Wait -UseExisting

VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
ApplyConfiguration,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer SERVER01 with user sid
S-1-5-21-124525095-708259637-1543119021-1282804.
VERBOSE: [SERVER01]:                            [] Starting consistency engine.
VERBOSE: [SERVER01]:                            [] Checking consistency for current configuration.
VERBOSE: [SERVER01]:                            [DSCEngine] Importing the module
C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\DscResources\MSFT_ServiceResource\MSFT
_ServiceResource.psm1 in force mode.
VERBOSE: [SERVER01]: LCM:  [ Start  Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ Start  Test     ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [[Service]Spooler] Importing the module MSFT_ServiceResource in
force mode.
VERBOSE: [SERVER01]: LCM:  [ End    Test     ]  [[Service]Spooler]  in 0.2540 seconds.
VERBOSE: [SERVER01]: LCM:  [ Skip   Set      ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ End    Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [] Consistency check completed.
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Time taken for configuration job to complete is 1.379 seconds
```

## <a name="see-also"></a>另請參閱

- [Azure 自動化 DSC 概觀](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [設定 SMB 提取伺服器](../pull-server/pullServerSMB.md)
- [設定提取用戶端](../pull-server/pullClientConfigID.md)
