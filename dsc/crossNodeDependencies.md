---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "指定跨節點相依性"
ms.openlocfilehash: 885c130fb050629aac4c072e18a147d77b9deb8f
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2017
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="baf03-103">指定跨節點相依性</span><span class="sxs-lookup"><span data-stu-id="baf03-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="baf03-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="baf03-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="baf03-105">DSC 提供特殊的資源 **WaitForAll**、**WaitForAny** 與 **WaitForSome**，可以用在設定中指定其他節點上設定的相依性。</span><span class="sxs-lookup"><span data-stu-id="baf03-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="baf03-106">這些資源的行為如下所示︰</span><span class="sxs-lookup"><span data-stu-id="baf03-106">The behavior of these resources is as follows:</span></span>

* <span data-ttu-id="baf03-107">**WaitForAll**︰如果指定的資源在定義於 **NodeName** 屬性中的所有目標節點上，皆為所需的狀態，即會成功。</span><span class="sxs-lookup"><span data-stu-id="baf03-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="baf03-108">**WaitForAny**︰如果指定的資源在定義於 **NodeName** 屬性中的至少一個目標節點上，為所需的狀態，即會成功。</span><span class="sxs-lookup"><span data-stu-id="baf03-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="baf03-109">**WaitForSome**：除了 **NodeName** 屬性外，指定一個 **NodeCount** 屬性。</span><span class="sxs-lookup"><span data-stu-id="baf03-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="baf03-110">如果資源至少有在最少的節點數目 (由 **NodeName** 屬性所定義的 **NodeCount** 指定) 上為所需的狀態，該資源即成功。</span><span class="sxs-lookup"><span data-stu-id="baf03-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="baf03-111">使用 WaitForXXXX 資源</span><span class="sxs-lookup"><span data-stu-id="baf03-111">Using WaitForXXXX resources</span></span>

<span data-ttu-id="baf03-112">若要使用 **WaitForXXXX** 資源，需要建立指定要等候之 DSC 資源與節點的該資源類型資源區塊。</span><span class="sxs-lookup"><span data-stu-id="baf03-112">To use the **WaitForXXXX** resources, you create a resource block of that resource type that specifies the DSC resource and node(s) to wait for.</span></span> <span data-ttu-id="baf03-113">然後使用 **DependsOn** 屬性 (在設定中的任一其他資源區塊中)，等候 **WaitForXXXX** 節點內指定的條件成功。</span><span class="sxs-lookup"><span data-stu-id="baf03-113">You then use the **DependsOn** property in any other resource blocks in your configuration to wait for the conditions specified in the **WaitForXXXX** node to succeed.</span></span>

<span data-ttu-id="baf03-114">例如，在下列設定中，目標節點正在等候 **xADDomain** 資源在 **MyDC** 節點上在 15 秒的間隔內最多重試 30 次完成，之後目標節點才能加入網域。</span><span class="sxs-lookup"><span data-stu-id="baf03-114">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

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

><span data-ttu-id="baf03-115">**注意︰**根據預設，WaitForXXX 資源會嘗試一次，然後才失敗。</span><span class="sxs-lookup"><span data-stu-id="baf03-115">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="baf03-116">雖然並非必要，但通常要指定重試間隔與計數。</span><span class="sxs-lookup"><span data-stu-id="baf03-116">Although it is not required, you will typically want to specify a retry interval and count.</span></span>

## <a name="see-also"></a><span data-ttu-id="baf03-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="baf03-117">See Also</span></span>
* [<span data-ttu-id="baf03-118">DSC 設定</span><span class="sxs-lookup"><span data-stu-id="baf03-118">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="baf03-119">DSC 資源</span><span class="sxs-lookup"><span data-stu-id="baf03-119">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="baf03-120">設定本機設定管理員</span><span class="sxs-lookup"><span data-stu-id="baf03-120">Configuring The Local Configuration Manager</span></span>](metaConfig.md)

