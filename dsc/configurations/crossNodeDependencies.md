---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 指定跨節點相依性
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400626"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="a0549-103">指定跨節點相依性</span><span class="sxs-lookup"><span data-stu-id="a0549-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="a0549-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a0549-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="a0549-105">DSC 提供特殊的資源 **WaitForAll**、**WaitForAny** 與 **WaitForSome**，可以用在設定中指定其他節點上設定的相依性。</span><span class="sxs-lookup"><span data-stu-id="a0549-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="a0549-106">這些資源的行為如下所示︰</span><span class="sxs-lookup"><span data-stu-id="a0549-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="a0549-107">**WaitForAll**:如果指定的資源所需的狀態中所定義的所有目標節點上會成功**NodeName**屬性。</span><span class="sxs-lookup"><span data-stu-id="a0549-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="a0549-108">**WaitForAny**:如果指定的資源處於預期狀態的至少其中一個定義的目標節點成功**NodeName**屬性。</span><span class="sxs-lookup"><span data-stu-id="a0549-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="a0549-109">**WaitForSome**:指定**NodeCount**屬性，除了**NodeName**屬性。</span><span class="sxs-lookup"><span data-stu-id="a0549-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="a0549-110">如果資源至少有在最少的節點數目 (由 **NodeName** 屬性所定義的 **NodeCount** 指定) 上為所需的狀態，該資源即成功。</span><span class="sxs-lookup"><span data-stu-id="a0549-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="a0549-111">語法</span><span class="sxs-lookup"><span data-stu-id="a0549-111">Syntax</span></span>

<span data-ttu-id="a0549-112">**WaitForAll**並**WaitForAny**資源共用相同的語法。</span><span class="sxs-lookup"><span data-stu-id="a0549-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="a0549-113">取代\<ResourceType\>在下列範例中使用**WaitForAny**或是**WaitForAll**。</span><span class="sxs-lookup"><span data-stu-id="a0549-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="a0549-114">像是**DependsOn**關鍵字，您必須設定為"[ResourceType] ResourceName"名稱的格式。</span><span class="sxs-lookup"><span data-stu-id="a0549-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="a0549-115">如果資源屬於個別[組態](configurations.md)，包括**ConfigurationName**格式化字串中"[ResourceType] ResourceName:: [ConfigurationName]:: [ConfigurationName]"。</span><span class="sxs-lookup"><span data-stu-id="a0549-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="a0549-116">**NodeName**電腦，或的節點，在其等候目前的資源。</span><span class="sxs-lookup"><span data-stu-id="a0549-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

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

<span data-ttu-id="a0549-117">**WaitForSome**資源至上面的範例，類似的語法，但新增**NodeCount**索引鍵。</span><span class="sxs-lookup"><span data-stu-id="a0549-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="a0549-118">**NodeCount**指出目前的資源應該等候的節點數。</span><span class="sxs-lookup"><span data-stu-id="a0549-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

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

<span data-ttu-id="a0549-119">所有**WaitForXXXX**將金鑰分享給下列語法。</span><span class="sxs-lookup"><span data-stu-id="a0549-119">All **WaitForXXXX** share the following syntax keys.</span></span>

<span data-ttu-id="a0549-120">| 屬性 | 描述 | |RetryIntervalSec |重試之前的秒數。</span><span class="sxs-lookup"><span data-stu-id="a0549-120">|  Property  |  Description   | | RetryIntervalSec| The number of seconds before retrying.</span></span> <span data-ttu-id="a0549-121">最小值為 1。 ||RetryCount |重試的次數上限。 ||ThrottleLimit |可同時連接的機器數目。</span><span class="sxs-lookup"><span data-stu-id="a0549-121">Minimum is 1.| | RetryCount| The maximum number of times to retry.| | ThrottleLimit| Number of machines to connect simultaneously.</span></span> <span data-ttu-id="a0549-122">預設值是`New-CimSession`預設。 | |DependsOn |指出必須執行另一個資源的設定，才能設定此資源。</span><span class="sxs-lookup"><span data-stu-id="a0549-122">Default is `New-CimSession` default.| | DependsOn | Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a0549-123">如需詳細資訊，請參閱 < [DependsOn](resource-depends-on.md)| |PsDscRunAsCredential |請參閱[使用使用者認證的 DSC](./runAsUser.md) |</span><span class="sxs-lookup"><span data-stu-id="a0549-123">For more information, see [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | See [Using DSC with User Credentials](./runAsUser.md) |</span></span>


## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="a0549-124">使用 WaitForXXXX 資源</span><span class="sxs-lookup"><span data-stu-id="a0549-124">Using WaitForXXXX resources</span></span>

<span data-ttu-id="a0549-125">每個**WaitForXXXX**資源等候指定的節點上完成指定的資源。</span><span class="sxs-lookup"><span data-stu-id="a0549-125">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span> <span data-ttu-id="a0549-126">相同的組態中的其他資源即可*而定* **WaitForXXXX**資源使用**DependsOn**索引鍵。</span><span class="sxs-lookup"><span data-stu-id="a0549-126">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="a0549-127">例如，在下列設定中，目標節點正在等候 **xADDomain** 資源在 **MyDC** 節點上在 15 秒的間隔內最多重試 30 次完成，之後目標節點才能加入網域。</span><span class="sxs-lookup"><span data-stu-id="a0549-127">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

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

<span data-ttu-id="a0549-128">當您編譯設定時，會產生兩個 「.mof 」 檔案。</span><span class="sxs-lookup"><span data-stu-id="a0549-128">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="a0549-129">這兩個 「.mof"檔案套用到使用的目標節點[Start-dscconfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span><span class="sxs-lookup"><span data-stu-id="a0549-129">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

><span data-ttu-id="a0549-130">**注意：** 預設 WaitForXXX 資源會嘗試一次，則失敗。</span><span class="sxs-lookup"><span data-stu-id="a0549-130">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="a0549-131">雖然您不需要，您通常會想要指定**RetryCount**並**RetryIntervalSec**。</span><span class="sxs-lookup"><span data-stu-id="a0549-131">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0549-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0549-132">See Also</span></span>

- [<span data-ttu-id="a0549-133">DSC 設定</span><span class="sxs-lookup"><span data-stu-id="a0549-133">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="a0549-134">使用資源相依性</span><span class="sxs-lookup"><span data-stu-id="a0549-134">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="a0549-135">DSC 資源</span><span class="sxs-lookup"><span data-stu-id="a0549-135">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="a0549-136">設定本機設定管理員</span><span class="sxs-lookup"><span data-stu-id="a0549-136">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
