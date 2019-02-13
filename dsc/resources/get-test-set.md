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
# <a name="get-test-set"></a><span data-ttu-id="0b179-103">Get-Test-Set</span><span class="sxs-lookup"><span data-stu-id="0b179-103">Get-Test-Set</span></span>

><span data-ttu-id="0b179-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0b179-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

![取得、測試及設定](/media/get-test-set.png)

<span data-ttu-id="0b179-106">會建構 PowerShell Desired State Configuration**取得**，**測試**，並**設定**程序。</span><span class="sxs-lookup"><span data-stu-id="0b179-106">PowerShell Desired State Configuration is constructed around a **Get**, **Test**, and **Set** process.</span></span> <span data-ttu-id="0b179-107">DSC[資源](resources.md)每個包含的方法可以完成上述各項作業。</span><span class="sxs-lookup"><span data-stu-id="0b179-107">DSC [resources](resources.md) each contains methods to complete each of these operations.</span></span> <span data-ttu-id="0b179-108">在 [組態](../configurations/configurations.md)，您定義填滿成為資源參數的索引鍵中的資源區塊**取得**，**測試**，和**設定**方法。</span><span class="sxs-lookup"><span data-stu-id="0b179-108">In a [Configuration](../configurations/configurations.md), you define resource blocks to fill in keys that become parameters for a resource's **Get**, **Test**, and **Set** methods.</span></span>

<span data-ttu-id="0b179-109">這是語法**服務**資源區塊。</span><span class="sxs-lookup"><span data-stu-id="0b179-109">This is the syntax for a **Service** resource block.</span></span> <span data-ttu-id="0b179-110">**服務**資源會設定 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="0b179-110">The **Service** resource configures Windows services.</span></span>

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

<span data-ttu-id="0b179-111">**取得**，**測試**，並**設定**方法**服務**資源會有接受這些值的參數區塊。</span><span class="sxs-lookup"><span data-stu-id="0b179-111">The **Get**, **Test**, and **Set** methods of the **Service** resource will have parameter blocks that accept these values.</span></span>

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
> <span data-ttu-id="0b179-112">語言和用來定義資源的方法會決定如何**取得**，**測試**，並**設定**會定義方法。</span><span class="sxs-lookup"><span data-stu-id="0b179-112">The language and method used to define the resource determines how the **Get**, **Test**, and **Set** methods will be defined.</span></span>

<span data-ttu-id="0b179-113">因為**服務**資源只有一個必要的索引鍵 (`Name`)，則**服務**區塊資源可能是這麼簡單：</span><span class="sxs-lookup"><span data-stu-id="0b179-113">Because the **Service** resource only has one required key (`Name`), a **Service** block resource could be as simple as this:</span></span>

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

<span data-ttu-id="0b179-114">當您編譯上述的組態時，就會產生 「.mof 」 檔案中儲存您指定的索引鍵的值。</span><span class="sxs-lookup"><span data-stu-id="0b179-114">When you compile the Configuration above, the values you specify for a key are stored in the ".mof" file that is generated.</span></span> <span data-ttu-id="0b179-115">如需詳細資訊，請參閱 < [MOF](/windows/desktop/wmisdk/managed-object-format--mof-)。</span><span class="sxs-lookup"><span data-stu-id="0b179-115">For more information, see [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>

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

<span data-ttu-id="0b179-116">套用時，[本機設定管理員](../managing-nodes/metaConfig.md)將 「 多工緩衝處理器 」 的值從".mof"檔案讀取，並將它傳遞給`-Name`參數**取得**，**測試**，並**設定**"MyService"執行個體的方法**服務**資源。</span><span class="sxs-lookup"><span data-stu-id="0b179-116">When applied, the [Local Configuration Manager](../managing-nodes/metaConfig.md) will read the value "Spooler" from the ".mof" file, and pass it to the `-Name` parameter of the **Get**, **Test**, and **Set** methods for the "MyService" instance of the **Service** resource.</span></span>

## <a name="get"></a><span data-ttu-id="0b179-117">取得</span><span class="sxs-lookup"><span data-stu-id="0b179-117">Get</span></span>

<span data-ttu-id="0b179-118">**取得**方法的資源，擷取資源的狀態，因為它在目標節點上進行設定。</span><span class="sxs-lookup"><span data-stu-id="0b179-118">The **Get** method of a resource, retrieves the state of the resource as it is configured on the target Node.</span></span> <span data-ttu-id="0b179-119">此狀態會當成[雜湊表](/powershell/module/microsoft.powershell.core/about/about_hash_tables)。</span><span class="sxs-lookup"><span data-stu-id="0b179-119">This state is returned as a [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span> <span data-ttu-id="0b179-120">索引鍵**雜湊表**會是可設定的值或參數，資源會接受。</span><span class="sxs-lookup"><span data-stu-id="0b179-120">The keys of the **hashtable** will be the configurable values, or parameters, the resource accepts.</span></span>

<span data-ttu-id="0b179-121">**取得**方法會直接對應至[Get-dscconfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0b179-121">The **Get** method maps directly to the [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="0b179-122">當您呼叫`Get-DSCConfiguration`，在 LCM 執行**取得**目前套用的設定中每個資源的方法。</span><span class="sxs-lookup"><span data-stu-id="0b179-122">When you call `Get-DSCConfiguration`, the LCM runs the **Get** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="0b179-123">LCM 會使用儲存在 「.mof"檔案做為參數，每個對應的資源執行個體的索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="0b179-123">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="0b179-124">這是範例輸出**服務**設定 「 多工緩衝處理器 」 服務的資源。</span><span class="sxs-lookup"><span data-stu-id="0b179-124">This is sample output from a **Service** resource that configures the "Spooler" service.</span></span>

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

<span data-ttu-id="0b179-125">輸出會顯示目前的值屬性可由設定**服務**資源。</span><span class="sxs-lookup"><span data-stu-id="0b179-125">The output shows the current value properties configurable by the **Service** resource.</span></span>

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

## <a name="test"></a><span data-ttu-id="0b179-126">Test</span><span class="sxs-lookup"><span data-stu-id="0b179-126">Test</span></span>

<span data-ttu-id="0b179-127">**測試**資源的方法會判斷目標節點是否與資源的目前相容*期望狀態*。</span><span class="sxs-lookup"><span data-stu-id="0b179-127">The **Test** method of a resource determines if the target node is currently compliant with the resource's *desired state*.</span></span> <span data-ttu-id="0b179-128">**測試**方法會傳回`$True`或`$False`只以指出節點是否符合規範。</span><span class="sxs-lookup"><span data-stu-id="0b179-128">The **Test** method returns `$True` or `$False` only to indicate whether the Node is compliant.</span></span>
<span data-ttu-id="0b179-129">當您呼叫[Test-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)，，LCM 會呼叫**測試**目前套用的設定中每個資源的方法。</span><span class="sxs-lookup"><span data-stu-id="0b179-129">When you call [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), the LCM calls the **Test** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="0b179-130">LCM 會使用儲存在 「.mof"檔案做為參數，每個對應的資源執行個體的索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="0b179-130">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="0b179-131">如果結果的任何個別的資源**測試**是`$False`，`Test-DSCConfiguration`傳回`$False`指出的節點不符合規範。</span><span class="sxs-lookup"><span data-stu-id="0b179-131">If the result of any individual resource's **Test** is `$False`, `Test-DSCConfiguration` returns `$False` indicating that the Node is not compliant.</span></span> <span data-ttu-id="0b179-132">如果所有的資源**測試**方法會傳回`$True`，`Test-DSCConfiguration`傳回`$True`表示節點為符合規範。</span><span class="sxs-lookup"><span data-stu-id="0b179-132">If all resource's **Test** methods return `$True`, `Test-DSCConfiguration` returns `$True` to indicate that the Node is compliant.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

<span data-ttu-id="0b179-133">在 PowerShell 5.0 中，從開始`-Detailed`參數已加入。</span><span class="sxs-lookup"><span data-stu-id="0b179-133">Beginning in PowerShell 5.0, the `-Detailed` parameter was added.</span></span> <span data-ttu-id="0b179-134">指定`-Detailed`會導致`Test-DSCConfiguration`傳回物件，其中包含集合的結果符合規範且不符合規範的資源。</span><span class="sxs-lookup"><span data-stu-id="0b179-134">Specifying `-Detailed` causes `Test-DSCConfiguration` to return an object containing collections of results for compliant, and non-compliant resources.</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

<span data-ttu-id="0b179-135">如需詳細資訊，請參閱[Test-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span><span class="sxs-lookup"><span data-stu-id="0b179-135">For more information, see [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span></span>

## <a name="set"></a><span data-ttu-id="0b179-136">設定</span><span class="sxs-lookup"><span data-stu-id="0b179-136">Set</span></span>

<span data-ttu-id="0b179-137">**設定**資源的方法會嘗試強制的節點，以符合規範的資源時*期望狀態*。</span><span class="sxs-lookup"><span data-stu-id="0b179-137">The **Set** method of a resource attempts to force the Node to become compliant with the resource's *desired state*.</span></span> <span data-ttu-id="0b179-138">**設定**方法僅供**具有等冪性**，這表示**設定**會多次執行，且一律取得相同的結果正確無誤。</span><span class="sxs-lookup"><span data-stu-id="0b179-138">The **Set** method is meant to be **idempotent**, which means that **Set** could be run multiple times and always get the same result without errors.</span></span>  <span data-ttu-id="0b179-139">當您執行[Start-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration)、 LCM 循環，透過目前套用的設定中每個資源。</span><span class="sxs-lookup"><span data-stu-id="0b179-139">When you run [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), the LCM cycles through each resource in the currently applied configuration.</span></span> <span data-ttu-id="0b179-140">LCM".mof 」 檔案中擷取目前的資源執行個體的索引鍵值，並使用它們做為參數**測試**方法。</span><span class="sxs-lookup"><span data-stu-id="0b179-140">The LCM retrieves key values for the current resource instance from the ".mof" file and uses them as parameters for the **Test** method.</span></span> <span data-ttu-id="0b179-141">如果**測試**方法會傳回`$True`，該節點是符合目前的資源，而**設定**方法會略過。</span><span class="sxs-lookup"><span data-stu-id="0b179-141">If the **Test** method returns `$True`, the Node is compliant with the current resource, and the **Set** method is skipped.</span></span> <span data-ttu-id="0b179-142">如果**測試**傳回`$False`，節點是不符合規範。</span><span class="sxs-lookup"><span data-stu-id="0b179-142">If the **Test** returns `$False`, the Node is non-compliant.</span></span>  <span data-ttu-id="0b179-143">LCM 資源執行個體的索引鍵會將值傳遞做為參數的資源**設定**節點還原為合規性的方法。</span><span class="sxs-lookup"><span data-stu-id="0b179-143">The LCM passes the resource instance's key values as parameters to the resource's **Set** method, restoring the Node to compliance.</span></span>

<span data-ttu-id="0b179-144">藉由指定`-Verbose`並`-Wait`參數，您可以觀看的進度`Start-DSCConfiguration`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0b179-144">By specifying the `-Verbose` and `-Wait` parameters, you can watch the progress of the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="0b179-145">在此範例中，節點是已經符合規範。</span><span class="sxs-lookup"><span data-stu-id="0b179-145">In this example, the Node is already compliant.</span></span> <span data-ttu-id="0b179-146">`Verbose`輸出指出**設定**方法已略過。</span><span class="sxs-lookup"><span data-stu-id="0b179-146">The `Verbose` output indicates that the **Set** method was skipped.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0b179-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b179-147">See also</span></span>

- [<span data-ttu-id="0b179-148">Azure 自動化 DSC 概觀</span><span class="sxs-lookup"><span data-stu-id="0b179-148">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="0b179-149">設定 SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="0b179-149">Setting up an SMB pull server</span></span>](../pull-server/pullServerSMB.md)
- [<span data-ttu-id="0b179-150">設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="0b179-150">Configuring a pull client</span></span>](../pull-server/pullClientConfigID.md)
