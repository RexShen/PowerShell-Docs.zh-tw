---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 指定跨節點相依性
description: DSC 提供特殊的資源，其可以用於設定中以指定其他節點之設定的相依性。
ms.openlocfilehash: a9fc09af922839b37db476c24c113efc5e3e8cb1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658494"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="e154d-104">指定跨節點相依性</span><span class="sxs-lookup"><span data-stu-id="e154d-104">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="e154d-105">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e154d-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="e154d-106">DSC 提供特殊的資源 **WaitForAll** 、 **WaitForAny** 與 **WaitForSome** ，可以用在設定中指定其他節點上設定的相依性。</span><span class="sxs-lookup"><span data-stu-id="e154d-106">DSC provides special resources, **WaitForAll** , **WaitForAny** , and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="e154d-107">這些資源的行為如下所示︰</span><span class="sxs-lookup"><span data-stu-id="e154d-107">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="e154d-108">**WaitForAll** ︰如果指定的資源在定義於 **NodeName** 屬性中的所有目標節點上，皆為所需的狀態，即會成功。</span><span class="sxs-lookup"><span data-stu-id="e154d-108">**WaitForAll** : Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="e154d-109">**WaitForAny** ︰如果指定的資源在定義於 **NodeName** 屬性中的至少一個目標節點上，為所需的狀態，即會成功。</span><span class="sxs-lookup"><span data-stu-id="e154d-109">**WaitForAny** : Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="e154d-110">**WaitForSome** ：除了 **NodeName** 屬性外，指定一個 **NodeCount** 屬性。</span><span class="sxs-lookup"><span data-stu-id="e154d-110">**WaitForSome** : Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="e154d-111">如果資源至少有在最少的節點數目 (由 **NodeName** 屬性所定義的 **NodeCount** 指定) 上為所需的狀態，該資源即成功。</span><span class="sxs-lookup"><span data-stu-id="e154d-111">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount** ) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="e154d-112">Syntax</span><span class="sxs-lookup"><span data-stu-id="e154d-112">Syntax</span></span>

<span data-ttu-id="e154d-113">**WaitForAll** 和 **WaitForAny** 資源共用相同的語法。</span><span class="sxs-lookup"><span data-stu-id="e154d-113">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="e154d-114">將下面範例中的 `<ResourceType>` 取代為 **WaitForAny** 或 **WaitForAll** 。</span><span class="sxs-lookup"><span data-stu-id="e154d-114">Replace `<ResourceType>` in the example below with either **WaitForAny** or **WaitForAll**.</span></span> <span data-ttu-id="e154d-115">與 **DependsOn** 關鍵字一樣，您必須將名稱格式化為 `[ResourceType]ResourceName`。</span><span class="sxs-lookup"><span data-stu-id="e154d-115">Like the **DependsOn** keyword, you will need to format the name as `[ResourceType]ResourceName`.</span></span> <span data-ttu-id="e154d-116">如果資源屬於個別的 [設定](configurations.md)，請在格式化的字串中加入 **ConfigurationName** ，例如 `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`。</span><span class="sxs-lookup"><span data-stu-id="e154d-116">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span></span> <span data-ttu-id="e154d-117">**NodeName** 是目前資源應該等候的電腦或 Node。</span><span class="sxs-lookup"><span data-stu-id="e154d-117">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

<span data-ttu-id="e154d-118">**WaitForSome** 資源與上述的範例擁有類似的語法，但多了 **NodeCount** 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="e154d-118">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="e154d-119">**NodeCount** 指出目前資源應等候的 Node 數目。</span><span class="sxs-lookup"><span data-stu-id="e154d-119">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

<span data-ttu-id="e154d-120">所有的 **WaitForXXXX** 都共用下列語法索引鍵。</span><span class="sxs-lookup"><span data-stu-id="e154d-120">All **WaitForXXXX** share the following syntax keys.</span></span>

|       <span data-ttu-id="e154d-121">屬性</span><span class="sxs-lookup"><span data-stu-id="e154d-121">Property</span></span>       |                                                                           <span data-ttu-id="e154d-122">描述</span><span class="sxs-lookup"><span data-stu-id="e154d-122">Description</span></span>                                                                           |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="e154d-123">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="e154d-123">RetryIntervalSec</span></span>     | <span data-ttu-id="e154d-124">進行重試之前的秒數。</span><span class="sxs-lookup"><span data-stu-id="e154d-124">The number of seconds before retrying.</span></span> <span data-ttu-id="e154d-125">最小值為 1。</span><span class="sxs-lookup"><span data-stu-id="e154d-125">Minimum is 1.</span></span>                                                                                                            |
| <span data-ttu-id="e154d-126">RetryCount</span><span class="sxs-lookup"><span data-stu-id="e154d-126">RetryCount</span></span>           | <span data-ttu-id="e154d-127">重試次數上限。</span><span class="sxs-lookup"><span data-stu-id="e154d-127">The maximum number of times to retry.</span></span>                                                                                                                           |
| <span data-ttu-id="e154d-128">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="e154d-128">ThrottleLimit</span></span>        | <span data-ttu-id="e154d-129">可同時連線的電腦數目。</span><span class="sxs-lookup"><span data-stu-id="e154d-129">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="e154d-130">預設值為 `New-CimSession` 預設值。</span><span class="sxs-lookup"><span data-stu-id="e154d-130">Default is `New-CimSession` default.</span></span>                                                                              |
| <span data-ttu-id="e154d-131">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e154d-131">DependsOn</span></span>            | <span data-ttu-id="e154d-132">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="e154d-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e154d-133">如需詳細資訊，請參閱 [DependsOn](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="e154d-133">For more information, see [DependsOn](resource-depends-on.md)</span></span> |
| <span data-ttu-id="e154d-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="e154d-134">PsDscRunAsCredential</span></span> | <span data-ttu-id="e154d-135">請參閱[以使用者認證執行 DSC](./runAsUser.md)</span><span class="sxs-lookup"><span data-stu-id="e154d-135">See [Using DSC with User Credentials](./runAsUser.md)</span></span>                                                                                                           |

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="e154d-136">使用 WaitForXXXX 資源</span><span class="sxs-lookup"><span data-stu-id="e154d-136">Using WaitForXXXX resources</span></span>

<span data-ttu-id="e154d-137">每個 **WaitForXXXX** 資源都會等候指定的資源在指定的 Node 上完成。</span><span class="sxs-lookup"><span data-stu-id="e154d-137">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span>
<span data-ttu-id="e154d-138">在相同 Configuration 上的其他資源，接著可以使用 **DependsOn** 索引鍵，「相依於」 **WaitForXXXX** 資源。</span><span class="sxs-lookup"><span data-stu-id="e154d-138">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="e154d-139">例如，在下列設定中，目標節點正在等候 **xADDomain** 資源在 **MyDC** 節點上在 15 秒的間隔內最多重試 30 次完成，之後目標節點才能加入網域。</span><span class="sxs-lookup"><span data-stu-id="e154d-139">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

<span data-ttu-id="e154d-140">根據預設， **WaitForXXX** 資源會嘗試一次，然後才失敗。</span><span class="sxs-lookup"><span data-stu-id="e154d-140">By default the **WaitForXXX** resources try one time and then fail.</span></span> <span data-ttu-id="e154d-141">雖然並非必要，但通常要指定 **RetryCount** 與 **RetryIntervalSec** 。</span><span class="sxs-lookup"><span data-stu-id="e154d-141">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

```powershell
Configuration JoinDomain
{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }
    }

    Node myDomainJoinedServer
    {
        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

<span data-ttu-id="e154d-142">當您編譯 Configuration 時，會產生兩個 ".mof" 檔案。</span><span class="sxs-lookup"><span data-stu-id="e154d-142">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="e154d-143">使用 [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet，將這兩個 ".mof" 檔案套用至目標 Node</span><span class="sxs-lookup"><span data-stu-id="e154d-143">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

> [!NOTE]
> <span data-ttu-id="e154d-144">**WaitForXXX** 資源使用 Windows 遠端管理來檢查其他節點的狀態。</span><span class="sxs-lookup"><span data-stu-id="e154d-144">**WaitForXXX** resources use Windows Remote Management to check the state of other Nodes.</span></span> <span data-ttu-id="e154d-145">如需 WinRM 連接埠和安全性需求的詳細資訊，請參閱 [PowerShell 遠端安全性考量](/powershell/scripting/learn/remoting/winrmsecurity)。</span><span class="sxs-lookup"><span data-stu-id="e154d-145">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

## <a name="see-also"></a><span data-ttu-id="e154d-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e154d-146">See Also</span></span>

- [<span data-ttu-id="e154d-147">DSC 設定</span><span class="sxs-lookup"><span data-stu-id="e154d-147">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="e154d-148">使用資源相依性</span><span class="sxs-lookup"><span data-stu-id="e154d-148">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="e154d-149">DSC 資源</span><span class="sxs-lookup"><span data-stu-id="e154d-149">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="e154d-150">設定本機設定管理員</span><span class="sxs-lookup"><span data-stu-id="e154d-150">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
