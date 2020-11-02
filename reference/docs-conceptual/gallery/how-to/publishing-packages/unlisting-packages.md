---
ms.date: 06/12/2017
title: 將套件移出清單
description: PowerShell 資源庫不支援使用者永久刪除套件。 這可讓其他人對您的套件採取相依性，而不需要擔心日後可能中斷。
ms.openlocfilehash: 738167011f64b5174df3504c8e1d06146f4c7db5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662414"
---
# <a name="unlisting-packages"></a><span data-ttu-id="38695-104">將套件移出清單</span><span class="sxs-lookup"><span data-stu-id="38695-104">Unlisting Packages</span></span>

<span data-ttu-id="38695-105">**為什麼從 PowerShell 資源庫移除套件未公開為選項？**</span><span class="sxs-lookup"><span data-stu-id="38695-105">**Why is removing a package from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="38695-106">PowerShell 資源庫不支援使用者永久刪除套件。</span><span class="sxs-lookup"><span data-stu-id="38695-106">The PowerShell Gallery does not support users permanently deleting their packages.</span></span> <span data-ttu-id="38695-107">這可讓其他人對您的套件採取相依性，而不需要擔心日後可能中斷。</span><span class="sxs-lookup"><span data-stu-id="38695-107">This enables others to take dependencies on your packages without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="38695-108">例如，如果 Pester 模組相依於 Azure 模組，但 Azure 模組已從資源庫移除，使用者就無法再使用 Pester 模組。</span><span class="sxs-lookup"><span data-stu-id="38695-108">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then users can no longer use the Pester module.</span></span>

<span data-ttu-id="38695-109">您可以加以取消列出，而不是移除套件。</span><span class="sxs-lookup"><span data-stu-id="38695-109">Instead of removing a package you can unlist it.</span></span>

<span data-ttu-id="38695-110">**在 PowerShell 資源庫將套件移出清單會如何？**</span><span class="sxs-lookup"><span data-stu-id="38695-110">**What does unlisting a package on PowerShell Gallery do?**</span></span>

<span data-ttu-id="38695-111">在 PowerShell 資源庫將模組或指令碼等套件移出清單，就會將其從 [套件] 索引標籤移除。此外，使用搜尋列將無法探索到移出清單的套件。</span><span class="sxs-lookup"><span data-stu-id="38695-111">Unlisting a package such as a module or script in the PowerShell Gallery removes it from the Packages tab. In addition, unlisted packages will not be discoverable using the search bar.</span></span> <span data-ttu-id="38695-112">只有指定套件的確切名稱與版本，才能下載移出清單的套件。</span><span class="sxs-lookup"><span data-stu-id="38695-112">The only way to download an unlisted package is to specify the exact name and version of the package.</span></span> <span data-ttu-id="38695-113">因為如此，將套件移出清單不會中斷相依其上的其他模組或指令碼。</span><span class="sxs-lookup"><span data-stu-id="38695-113">Because of this, the unlisting of a package will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="38695-114">若要將您的套件移出清單，請前往套件詳細資料頁面，然後選取 [刪除模組]。</span><span class="sxs-lookup"><span data-stu-id="38695-114">To unlist your package, visit the package details page and select 'Delete Module'.</span></span> <span data-ttu-id="38695-115">取消選取 [列出] 核取方塊，然後選取 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="38695-115">Uncheck the 'Listed' checkbox, and select 'Save'.</span></span>

<span data-ttu-id="38695-116">**如何移除套件？**</span><span class="sxs-lookup"><span data-stu-id="38695-116">**How can I remove a package?**</span></span>

<span data-ttu-id="38695-117">如果您遇到必須刪除套件的情況，請連絡 PowerShell 資源庫系統管理員。</span><span class="sxs-lookup"><span data-stu-id="38695-117">If you experience a scenario where package deletion is necessary, contact the PowerShell Gallery Administrators.</span></span> <span data-ttu-id="38695-118">合理的刪除案例為：</span><span class="sxs-lookup"><span data-stu-id="38695-118">Valid deletion scenarios are:</span></span>

- <span data-ttu-id="38695-119">侵害著作權的問題。</span><span class="sxs-lookup"><span data-stu-id="38695-119">Issues of copyright infringement.</span></span>
- <span data-ttu-id="38695-120">套件包含可能有害的內容。</span><span class="sxs-lookup"><span data-stu-id="38695-120">Package contains potentially harmful content.</span></span>
- <span data-ttu-id="38695-121">套件包含敏感性資料。</span><span class="sxs-lookup"><span data-stu-id="38695-121">Package contains sensitive data.</span></span>

<span data-ttu-id="38695-122">若要提交「刪除套件要求」給 PowerShell 資源庫系統管理員，請前往套件的詳細資料頁面，然後選取 [連絡支援服務]。</span><span class="sxs-lookup"><span data-stu-id="38695-122">To submit a Delete Package Request to the PowerShell Gallery Administrators, visit your package's detail page and select Contact Support.</span></span>
