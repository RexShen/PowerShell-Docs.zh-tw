---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 7a1725e3858c59a6d31699add22b042359c48463
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676853"
---
# <a name="separation-of-node-and-configuration-ids"></a><span data-ttu-id="18a1d-102">隔離節點和設定識別碼</span><span class="sxs-lookup"><span data-stu-id="18a1d-102">Separation of Node and Configuration IDs</span></span>

## <a name="overview"></a><span data-ttu-id="18a1d-103">概觀</span><span class="sxs-lookup"><span data-stu-id="18a1d-103">Overview</span></span>

<span data-ttu-id="18a1d-104">為了在 Pull 模式中使用 DSC 時提供更有彈性且有效率的體驗，我們在此版本中加入了多種功能。</span><span class="sxs-lookup"><span data-stu-id="18a1d-104">In order to provide a more flexible and streamlined experience when using DSC in Pull mode, we have added a number of features in this release.</span></span> <span data-ttu-id="18a1d-105">這些功能可讓您更有彈性地輕鬆設定及部署跨多個節點的設定，同時仍然可以個別追蹤每個節點的狀態及報告資訊。</span><span class="sxs-lookup"><span data-stu-id="18a1d-105">These features are intended to allow you to have the flexibility to easily setup and deploy configurations across multiple nodes, while still tracking status and reporting information for each node individually.</span></span>
<span data-ttu-id="18a1d-106">這些功能如下所示︰</span><span class="sxs-lookup"><span data-stu-id="18a1d-106">These features are as follows:</span></span>

* <span data-ttu-id="18a1d-107">用來識別電腦設定的設定名稱。</span><span class="sxs-lookup"><span data-stu-id="18a1d-107">A configuration name which identifies the configuration for a computer.</span></span> <span data-ttu-id="18a1d-108">此名稱可由多個目標節點共用</span><span class="sxs-lookup"><span data-stu-id="18a1d-108">This name can be shared by multiple target nodes</span></span>
* <span data-ttu-id="18a1d-109">可唯一識別單一節點的代理程式識別碼</span><span class="sxs-lookup"><span data-stu-id="18a1d-109">An agent ID which uniquely identifies a single node</span></span>
* <span data-ttu-id="18a1d-110">只在目標節點第一次連線到提取伺服器時發生的註冊步驟</span><span class="sxs-lookup"><span data-stu-id="18a1d-110">A registration step which only occurs the first time a target node connects to a pull server</span></span>

<span data-ttu-id="18a1d-111">**注意︰** 這些功能已經加入，而且不會取代現有的提取功能和概念。</span><span class="sxs-lookup"><span data-stu-id="18a1d-111">**Note:** These features and functionality have been added and do not replace the existing pull features and concepts.</span></span> <span data-ttu-id="18a1d-112">您可以使用這些新功能或具有此版本中發送之新提取伺服器的舊功能。</span><span class="sxs-lookup"><span data-stu-id="18a1d-112">You can use these new features or the older ones with the new pull server shipping in this release.</span></span>

<span data-ttu-id="18a1d-113">如需詳細資訊，請參閱[使用設定名稱設定提取用戶端](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)。</span><span class="sxs-lookup"><span data-stu-id="18a1d-113">For more information, see [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>
