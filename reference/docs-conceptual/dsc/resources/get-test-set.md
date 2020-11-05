---
ms.date: 07/08/2020
keywords: dsc,powershell,設定,安裝
title: Get-Test-Set
description: 此文章說明如何在 DSC 設定中實作 Get、Test 與 Set 方法。
ms.openlocfilehash: e0da1452a1237c550f52a4a4f9e4400f801ed7cd
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646806"
---
# <a name="get-test-set"></a>Get-Test-Set

>適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

PowerShell 預期狀態設定是圍繞著 **取得** 、 **測試** 及 **設定** 流程所建構的。 每個 DSC [資源](resources.md)均包含可用以完成上述各項作業的方法。
在 [設定](../configurations/configurations.md)中，您會定義資源區塊來填滿索引鍵，以成為適用於資源之 **取得** 、 **測試** 及 **設定** 方法的參數。

這是適用於 **服務** 資源區塊的語法。 **服務** 資源會設定 Windows 服務。

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

**服務** 資源的 **取得** 、 **測試** 及 **設定** 方法將具備可接受這些值的參數區塊。

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
> 用來定義資源的語言和方法會決定將如何定義 **取得** 、 **測試** 及 **設定** 方法。

因為 **服務** 資源只有一個必要的索引鍵 (`Name`)，所以 **服務** 區塊資源可能如下所示般簡單：

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

當編譯上述組態時，您為索引鍵指定的值會儲存在所產生 `.mof` 檔案中。 如需詳細資訊，請參閱 [MOF](/windows/desktop/wmisdk/managed-object-format--mof-)。

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

套用時， [本機設定管理員](../managing-nodes/metaConfig.md) (LCM) 會從 `.mof` 檔案讀取值 "Spooler"，傳遞給 **Service** 資源其 "MyService" 執行個體的 **Get** 、 **Test** 和 **Set** 方法的 **Name** 參數。

## <a name="get"></a>Get

資源的 **取得** 方法會在目標節點上設定資源時擷取其狀態。 此狀態會當成[雜湊表](/powershell/module/microsoft.powershell.core/about/about_hash_tables)傳回。 **雜湊表** 的索引鍵將是資源接受的可設定值或參數。

**取得** 方法會直接對應至 [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) Cmdlet。
當您呼叫 `Get-DSCConfiguration` 時，LCM 會在目前套用的設定中執行每個資源的 **取得** 方法。 LCM 會使用儲存在 `.mof` 檔案中的索引鍵值，以作為每個對應資源執行個體的參數。

這是設定 "Spooler" 服務的 **服務** 資源範例輸出。

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
                       this service, you won't be able to print or see your printers.
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

輸出會顯示目前可由 **服務** 資源設定的值屬性。

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

## <a name="test"></a>測試

資源的 **測試** 方法會判斷目標節點目前是否符合資源「期望狀態」的規範。 **測試** 方法只會傳回 `$true` 或 `$false`，以指出節點是否符合規範。 當您呼叫 [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) 時，LCM 會在目前套用的設定中呼叫每個資源的 **取得** 方法。 LCM 會使用儲存於 ".mof" 檔案的索引鍵值作為每個對應資源執行個體的參數。

如果任何個別資源的 **測試** 結果是 `$false`，`Test-DSCConfiguration` 會傳回 `$false`，指出節點不符合規範。 如果所有資源的 **測試** 方法會傳回 `$true`，`Test-DSCConfiguration` 會傳回 `$true`，以指出節點符合規範。

```powershell
Test-DSCConfiguration
```

```output
True
```

從 PowerShell 5.0 開始，即已新增 **Detailed** 參數。 指定 **Detailed** 會導致 `Test-DSCConfiguration` 傳回物件，其包含符合規範及不符合規範的資源結果集合。

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

如需詳細資訊，請參閱 [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)。

## <a name="set"></a>設定

資源的 **設定** 方法會嘗試強制節點符合資源「期望狀態」的規範。 **設定** 方法意味著 **等冪** ，這表示 **設定** 會多次執行，且一律取得相同結果且不會有任何錯誤。 當您執行 [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration) 時，LCM 會在目前套用的設定中循環執行每個資源。 LCM 會在 ".mof" 檔案中擷取目前資源執行個體的索引鍵值，並使用它們作為 **測試** 方法的參數。 如果 **測試** 方法傳回 `$true`，則該節點符合目前資源的規範，且會跳過 **設定** 方法。 如果 **測試** 傳回 `$false`，則節點不符合規範。 LCM 會將資源執行個體的索引鍵值當作參數傳遞給資源的 **設定** 方法，還原節點以符合規範。

指定 **Verbose** 和 **Wait** 參數，即可監看 `Start-DSCConfiguration` Cmdlet 的進度。 在此範例中，節點已經符合規範。 `Verbose` 輸出指出已跳過 **設定** 方法。

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

- [Azure 自動化 DSC 概觀](/azure/automation/automation-dsc-overview)
- [設定 SMB 提取伺服器](../pull-server/pullServerSMB.md)
- [設定提取用戶端](../pull-server/pullClientConfigID.md)
