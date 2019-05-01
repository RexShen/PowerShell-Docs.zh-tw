---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 指定跨節點相依性
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080198"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="ec1cf-103">指定跨節點相依性</span><span class="sxs-lookup"><span data-stu-id="ec1cf-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="ec1cf-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ec1cf-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="ec1cf-105">DSC 提供特殊的資源 **WaitForAll**、**WaitForAny** 與 **WaitForSome**，可以用在設定中指定其他節點上設定的相依性。</span><span class="sxs-lookup"><span data-stu-id="ec1cf-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="ec1cf-106">這些資源的行為如下所示︰</span><span class="sxs-lookup"><span data-stu-id="ec1cf-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="ec1cf-107">**WaitForAll**：如果指定的資源在定義於 **NodeName** 屬性中的所有目標節點上，皆為所需的狀態，即會成功。</span><span class="sxs-lookup"><span data-stu-id="ec1cf-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="ec1cf-108">**WaitForAny**：如果指定的資源在定義於 **NodeName** 屬性中的至少一個目標節點上，為所需的狀態，即會成功。</span><span class="sxs-lookup"><span data-stu-id="ec1cf-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="ec1cf-109">**WaitForSome**：除了 **NodeName** 屬性外，指定一個 **NodeCount** 屬性。</span><span class="sxs-lookup"><span data-stu-id="ec1cf-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="ec1cf-110">如果資源至少有在最少的節點數目 (由 **NodeName** 屬性所定義的 **NodeCount** 指定) 上為所需的狀態，該資源即成功。</span><span class="sxs-lookup"><span data-stu-id="ec1cf-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="ec1cf-111">語法</span><span class="sxs-lookup"><span data-stu-id="ec1cf-111">Syntax</span></span>

<span data-ttu-id="ec1cf-112">**WaitForAll** 和 **WaitForAny** 資源共用相同的語法。</span><span class="sxs-lookup"><span data-stu-id="ec1cf-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="ec1cf-113">在以下範例中使用 **WaitForAny** 或 **WaitForAll** 取代 \<ResourceType\>。</span><span class="sxs-lookup"><span data-stu-id="ec1cf-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="ec1cf-114">和 **DependsOn** 關鍵字一樣，您必須將名稱格式化為 "[ResourceType]ResourceName"。</span><span class="sxs-lookup"><span data-stu-id="ec1cf-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="ec1cf-115">如果資源屬於個別的 [Configuration](configurations.md)，請在格式化的字串中加入 **ConfigurationName**，例如 "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]"。</span><span class="sxs-lookup"><span data-stu-id="ec1cf-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="ec1cf-116">**NodeName** 是目前資源應該等候的電腦或 Node。</span><span class="sxs-lookup"><span data-stu-id="ec1cf-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

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

<span data-ttu-id="ec1cf-117">**WaitForSome** 資源與上述的範例擁有類似的語法，但多了 **NodeCount** 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="ec1cf-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="ec1cf-118">**NodeCount** 指出目前資源應等候的 Node 數目。</span><span class="sxs-lookup"><span data-stu-id="ec1cf-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

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

<span data-ttu-id="ec1cf-119">所有的 **WaitForXXXX** 都共用下列語法索引鍵。</span><span class="sxs-lookup"><span data-stu-id="ec1cf-119">All **WaitForXXXX** share the following syntax keys.</span></span>

<span data-ttu-id="ec1cf-120">|  屬性  |  描述   | | RetryIntervalSec| 重試之前的秒數。</span><span class="sxs-lookup"><span data-stu-id="ec1cf-120">|  Property  |  Description   | | RetryIntervalSec| The number of seconds before retrying.</span></span> <span data-ttu-id="ec1cf-121">最小值為 1。| | RetryCount| 重試的次數上限。| | ThrottleLimit| 可同時連線的電腦數目。</span><span class="sxs-lookup"><span data-stu-id="ec1cf-121">Minimum is 1.| | RetryCount| The maximum number of times to retry.| | ThrottleLimit| Number of machines to connect simultaneously.</span></span> <span data-ttu-id="ec1cf-122">預設值為 `New-CimSession`。| | DependsOn | 表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="ec1cf-122">Default is `New-CimSession` default.| | DependsOn | Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ec1cf-123">如需詳細資訊，請參閱 [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | 請參閱[使用 DSC 搭配使用者認證](./runAsUser.md) |</span><span class="sxs-lookup"><span data-stu-id="ec1cf-123">For more information, see [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | See [Using DSC with User Credentials](./runAsUser.md) |</span></span>


## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="ec1cf-124">使用 WaitForXXXX 資源</span><span class="sxs-lookup"><span data-stu-id="ec1cf-124">Using WaitForXXXX resources</span></span>

<span data-ttu-id="ec1cf-125">每個 **WaitForXXXX** 資源都會等候指定的資源在指定的 Node 上完成。</span><span class="sxs-lookup"><span data-stu-id="ec1cf-125">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span> <span data-ttu-id="ec1cf-126">在相同 Configuration 上的其他資源，接著可以使用 **DependsOn** 索引鍵，「相依於」**WaitForXXXX** 資源。</span><span class="sxs-lookup"><span data-stu-id="ec1cf-126">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="ec1cf-127">例如，在下列設定中，目標節點正在等候 **xADDomain** 資源在 **MyDC** 節點上在 15 秒的間隔內最多重試 30 次完成，之後目標節點才能加入網域。</span><span class="sxs-lookup"><span data-stu-id="ec1cf-127">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

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

<span data-ttu-id="ec1cf-128">當您編譯 Configuration 時，會產生兩個 ".mof" 檔案。</span><span class="sxs-lookup"><span data-stu-id="ec1cf-128">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="ec1cf-129">使用 [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet，將這兩個 ".mof" 檔案套用至目標 Node</span><span class="sxs-lookup"><span data-stu-id="ec1cf-129">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

><span data-ttu-id="ec1cf-130">**注意：** 根據預設，WaitForXXX 資源會嘗試一次，然後才失敗。</span><span class="sxs-lookup"><span data-stu-id="ec1cf-130">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="ec1cf-131">雖然並非必要，但通常要指定 **RetryCount** 與 **RetryIntervalSec**。</span><span class="sxs-lookup"><span data-stu-id="ec1cf-131">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec1cf-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec1cf-132">See Also</span></span>

- [<span data-ttu-id="ec1cf-133">DSC 設定</span><span class="sxs-lookup"><span data-stu-id="ec1cf-133">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="ec1cf-134">使用資源相依性</span><span class="sxs-lookup"><span data-stu-id="ec1cf-134">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="ec1cf-135">DSC 資源</span><span class="sxs-lookup"><span data-stu-id="ec1cf-135">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="ec1cf-136">設定本機設定管理員</span><span class="sxs-lookup"><span data-stu-id="ec1cf-136">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
