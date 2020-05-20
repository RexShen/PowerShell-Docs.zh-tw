---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: Get-Test-Set
ms.openlocfilehash: bf409f71c07c434fbc7389789e16575868d21b42
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278407"
---
# <a name="get-test-set"></a><span data-ttu-id="466f4-103">Get-Test-Set</span><span class="sxs-lookup"><span data-stu-id="466f4-103">Get-Test-Set</span></span>

><span data-ttu-id="466f4-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="466f4-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

![取得、測試及設定](media/get-test-set/get-test-set.png)

<span data-ttu-id="466f4-106">PowerShell 預期狀態設定是圍繞著**取得**、**測試**及**設定**流程所建構的。</span><span class="sxs-lookup"><span data-stu-id="466f4-106">PowerShell Desired State Configuration is constructed around a **Get**, **Test**, and **Set** process.</span></span> <span data-ttu-id="466f4-107">每個 DSC [資源](resources.md)均包含可用以完成上述各項作業的方法。</span><span class="sxs-lookup"><span data-stu-id="466f4-107">DSC [resources](resources.md) each contains methods to complete each of these operations.</span></span> <span data-ttu-id="466f4-108">在[設定](../configurations/configurations.md)中，您會定義資源區塊來填滿索引鍵，以成為適用於資源之**取得**、**測試**及**設定**方法的參數。</span><span class="sxs-lookup"><span data-stu-id="466f4-108">In a [Configuration](../configurations/configurations.md), you define resource blocks to fill in keys that become parameters for a resource's **Get**, **Test**, and **Set** methods.</span></span>

<span data-ttu-id="466f4-109">這是適用於**服務**資源區塊的語法。</span><span class="sxs-lookup"><span data-stu-id="466f4-109">This is the syntax for a **Service** resource block.</span></span> <span data-ttu-id="466f4-110">**服務**資源會設定 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="466f4-110">The **Service** resource configures Windows services.</span></span>

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

<span data-ttu-id="466f4-111">**服務**資源的**取得**、**測試**及**設定**方法將具備可接受這些值的參數區塊。</span><span class="sxs-lookup"><span data-stu-id="466f4-111">The **Get**, **Test**, and **Set** methods of the **Service** resource will have parameter blocks that accept these values.</span></span>

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
> <span data-ttu-id="466f4-112">用來定義資源的語言和方法會決定將如何定義**取得**、**測試**及**設定**方法。</span><span class="sxs-lookup"><span data-stu-id="466f4-112">The language and method used to define the resource determines how the **Get**, **Test**, and **Set** methods will be defined.</span></span>

<span data-ttu-id="466f4-113">因為**服務**資源只有一個必要的索引鍵 (`Name`)，所以**服務**區塊資源可能如下所示般簡單：</span><span class="sxs-lookup"><span data-stu-id="466f4-113">Because the **Service** resource only has one required key (`Name`), a **Service** block resource could be as simple as this:</span></span>

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

<span data-ttu-id="466f4-114">當您編譯上述設定時，會將您為索引鍵指定的值儲存於產生的 ".mof" 檔案中。</span><span class="sxs-lookup"><span data-stu-id="466f4-114">When you compile the Configuration above, the values you specify for a key are stored in the ".mof" file that is generated.</span></span> <span data-ttu-id="466f4-115">如需詳細資訊，請參閱 [MOF](/windows/desktop/wmisdk/managed-object-format--mof-)。</span><span class="sxs-lookup"><span data-stu-id="466f4-115">For more information, see [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>

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

<span data-ttu-id="466f4-116">套用時，[本機設定管理員](../managing-nodes/metaConfig.md) (LCM) 會從 ".mof" 檔案讀取值 "Spooler"，並針對 **Service** 資源的 "MyService" 執行個體，將它傳遞給 **Get**、**Test** 及 **Set** 方法的 `-Name` 參數。</span><span class="sxs-lookup"><span data-stu-id="466f4-116">When applied, the [Local Configuration Manager](../managing-nodes/metaConfig.md) (LCM) will read the value "Spooler" from the ".mof" file, and pass it to the `-Name` parameter of the **Get**, **Test**, and **Set** methods for the "MyService" instance of the **Service** resource.</span></span>

## <a name="get"></a><span data-ttu-id="466f4-117">Get</span><span class="sxs-lookup"><span data-stu-id="466f4-117">Get</span></span>

<span data-ttu-id="466f4-118">資源的**取得**方法會在目標節點上設定資源時擷取其狀態。</span><span class="sxs-lookup"><span data-stu-id="466f4-118">The **Get** method of a resource, retrieves the state of the resource as it is configured on the target Node.</span></span> <span data-ttu-id="466f4-119">此狀態會當成[雜湊表](/powershell/module/microsoft.powershell.core/about/about_hash_tables)傳回。</span><span class="sxs-lookup"><span data-stu-id="466f4-119">This state is returned as a [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span> <span data-ttu-id="466f4-120">**雜湊表**的索引鍵將是資源接受的可設定值或參數。</span><span class="sxs-lookup"><span data-stu-id="466f4-120">The keys of the **hashtable** will be the configurable values, or parameters, the resource accepts.</span></span>

<span data-ttu-id="466f4-121">**取得**方法會直接對應至 [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="466f4-121">The **Get** method maps directly to the [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="466f4-122">當您呼叫 `Get-DSCConfiguration` 時，LCM 會在目前套用的設定中執行每個資源的**取得**方法。</span><span class="sxs-lookup"><span data-stu-id="466f4-122">When you call `Get-DSCConfiguration`, the LCM runs the **Get** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="466f4-123">LCM 會使用儲存於 ".mof" 檔案的索引鍵值作為每個對應資源執行個體的參數。</span><span class="sxs-lookup"><span data-stu-id="466f4-123">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="466f4-124">這是設定 "Spooler" 服務的**服務**資源範例輸出。</span><span class="sxs-lookup"><span data-stu-id="466f4-124">This is sample output from a **Service** resource that configures the "Spooler" service.</span></span>

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

<span data-ttu-id="466f4-125">輸出會顯示目前可由**服務**資源設定的值屬性。</span><span class="sxs-lookup"><span data-stu-id="466f4-125">The output shows the current value properties configurable by the **Service** resource.</span></span>

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

## <a name="test"></a><span data-ttu-id="466f4-126">測試</span><span class="sxs-lookup"><span data-stu-id="466f4-126">Test</span></span>

<span data-ttu-id="466f4-127">資源的**測試**方法會判斷目標節點目前是否符合資源「期望狀態」  的規範。</span><span class="sxs-lookup"><span data-stu-id="466f4-127">The **Test** method of a resource determines if the target node is currently compliant with the resource's *desired state*.</span></span> <span data-ttu-id="466f4-128">**測試**方法只會傳回 `$True` 或 `$False`，以指出節點是否符合規範。</span><span class="sxs-lookup"><span data-stu-id="466f4-128">The **Test** method returns `$True` or `$False` only to indicate whether the Node is compliant.</span></span>
<span data-ttu-id="466f4-129">當您呼叫 [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) 時，LCM 會在目前套用的設定中呼叫每個資源的**取得**方法。</span><span class="sxs-lookup"><span data-stu-id="466f4-129">When you call [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), the LCM calls the **Test** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="466f4-130">LCM 會使用儲存於 ".mof" 檔案的索引鍵值作為每個對應資源執行個體的參數。</span><span class="sxs-lookup"><span data-stu-id="466f4-130">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="466f4-131">如果任何個別資源的**測試**結果是 `$False`，`Test-DSCConfiguration` 會傳回 `$False`，指出節點不符合規範。</span><span class="sxs-lookup"><span data-stu-id="466f4-131">If the result of any individual resource's **Test** is `$False`, `Test-DSCConfiguration` returns `$False` indicating that the Node is not compliant.</span></span> <span data-ttu-id="466f4-132">如果所有資源的**測試**方法會傳回 `$True`，`Test-DSCConfiguration` 會傳回 `$True`，以指出節點符合規範。</span><span class="sxs-lookup"><span data-stu-id="466f4-132">If all resource's **Test** methods return `$True`, `Test-DSCConfiguration` returns `$True` to indicate that the Node is compliant.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

<span data-ttu-id="466f4-133">從 PowerShell 5.0 開始，已新增 `-Detailed` 參數。</span><span class="sxs-lookup"><span data-stu-id="466f4-133">Beginning in PowerShell 5.0, the `-Detailed` parameter was added.</span></span> <span data-ttu-id="466f4-134">指定 `-Detailed` 會導致 `Test-DSCConfiguration` 傳回物件，其中包含符合規範的結果集合及不符合規範的資源。</span><span class="sxs-lookup"><span data-stu-id="466f4-134">Specifying `-Detailed` causes `Test-DSCConfiguration` to return an object containing collections of results for compliant, and non-compliant resources.</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

<span data-ttu-id="466f4-135">如需詳細資訊，請參閱 [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)。</span><span class="sxs-lookup"><span data-stu-id="466f4-135">For more information, see [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span></span>

## <a name="set"></a><span data-ttu-id="466f4-136">Set</span><span class="sxs-lookup"><span data-stu-id="466f4-136">Set</span></span>

<span data-ttu-id="466f4-137">資源的**設定**方法會嘗試強制節點符合資源「期望狀態」  的規範。</span><span class="sxs-lookup"><span data-stu-id="466f4-137">The **Set** method of a resource attempts to force the Node to become compliant with the resource's *desired state*.</span></span> <span data-ttu-id="466f4-138">**設定**方法意味著**等冪**，這表示**設定**會多次執行，且一律取得相同結果且不會有任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="466f4-138">The **Set** method is meant to be **idempotent**, which means that **Set** could be run multiple times and always get the same result without errors.</span></span>  <span data-ttu-id="466f4-139">當您執行 [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration) 時，LCM 會在目前套用的設定中循環執行每個資源。</span><span class="sxs-lookup"><span data-stu-id="466f4-139">When you run [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), the LCM cycles through each resource in the currently applied configuration.</span></span> <span data-ttu-id="466f4-140">LCM 會在 ".mof" 檔案中擷取目前資源執行個體的索引鍵值，並使用它們作為**測試**方法的參數。</span><span class="sxs-lookup"><span data-stu-id="466f4-140">The LCM retrieves key values for the current resource instance from the ".mof" file and uses them as parameters for the **Test** method.</span></span> <span data-ttu-id="466f4-141">如果**測試**方法傳回 `$True`，則該節點符合目前資源的規範，且會跳過**設定**方法。</span><span class="sxs-lookup"><span data-stu-id="466f4-141">If the **Test** method returns `$True`, the Node is compliant with the current resource, and the **Set** method is skipped.</span></span> <span data-ttu-id="466f4-142">如果**測試**傳回 `$False`，則節點不符合規範。</span><span class="sxs-lookup"><span data-stu-id="466f4-142">If the **Test** returns `$False`, the Node is non-compliant.</span></span>  <span data-ttu-id="466f4-143">LCM 會將資源執行個體的索引鍵值當作參數傳遞給資源的**設定**方法，還原節點以符合規範。</span><span class="sxs-lookup"><span data-stu-id="466f4-143">The LCM passes the resource instance's key values as parameters to the resource's **Set** method, restoring the Node to compliance.</span></span>

<span data-ttu-id="466f4-144">藉由指定 `-Verbose` 和 `-Wait` 參數，您可以監看 `Start-DSCConfiguration` Cmdlet 的進度。</span><span class="sxs-lookup"><span data-stu-id="466f4-144">By specifying the `-Verbose` and `-Wait` parameters, you can watch the progress of the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="466f4-145">在此範例中，節點已經符合規範。</span><span class="sxs-lookup"><span data-stu-id="466f4-145">In this example, the Node is already compliant.</span></span> <span data-ttu-id="466f4-146">`Verbose` 輸出指出已跳過**設定**方法。</span><span class="sxs-lookup"><span data-stu-id="466f4-146">The `Verbose` output indicates that the **Set** method was skipped.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="466f4-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="466f4-147">See also</span></span>

- [<span data-ttu-id="466f4-148">Azure 自動化 DSC 概觀</span><span class="sxs-lookup"><span data-stu-id="466f4-148">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="466f4-149">設定 SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="466f4-149">Setting up an SMB pull server</span></span>](../pull-server/pullServerSMB.md)
- [<span data-ttu-id="466f4-150">設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="466f4-150">Configuring a pull client</span></span>](../pull-server/pullClientConfigID.md)
