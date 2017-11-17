---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_unlist_items
ms.openlocfilehash: 8fa09c77e144f14bf0fd3493dff7650897100715
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="unlisting-items"></a><span data-ttu-id="2e12e-103">將項目從清單移除</span><span class="sxs-lookup"><span data-stu-id="2e12e-103">Unlisting items</span></span>

<span data-ttu-id="2e12e-104">**為什麼從 PowerShell 資源庫移除項目未公開為選項？**</span><span class="sxs-lookup"><span data-stu-id="2e12e-104">**Why is removing an item from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="2e12e-105">PowerShell 資源庫不支援使用者永久刪除項目。</span><span class="sxs-lookup"><span data-stu-id="2e12e-105">The PowerShell Gallery does not support users permanently deleting their items.</span></span> <span data-ttu-id="2e12e-106">這可讓其他人對您的項目採取相依性，而不需要擔心日後可能中斷。</span><span class="sxs-lookup"><span data-stu-id="2e12e-106">This enables others to take dependencies on your items without worrying about possible breaks in the future.</span></span> <span data-ttu-id="2e12e-107">例如，如果 Pester 模組相依於 Azure 模組，但 Azure 模組已從資源庫移除，使用者就無法再使用 Pester 模組。</span><span class="sxs-lookup"><span data-stu-id="2e12e-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="2e12e-108">與其移除項目，您可以改為將其移出清單。</span><span class="sxs-lookup"><span data-stu-id="2e12e-108">Instead of removing an item, however, you can unlist it instead.</span></span>

<span data-ttu-id="2e12e-109">**在 PowerShell 資源庫將項目移出清單會如何？**</span><span class="sxs-lookup"><span data-stu-id="2e12e-109">**What does unlisting an item on PowerShell Gallery do?**</span></span>

<span data-ttu-id="2e12e-110">在 PowerShell 資源庫將模組或指令碼等項目移出清單，就會將其從 [項目] 索引標籤移除。</span><span class="sxs-lookup"><span data-stu-id="2e12e-110">Unlisting an item such as module or script on PowerShell Gallery will remove it from the Items tab.</span></span>
<span data-ttu-id="2e12e-111">此外，使用搜尋列將無法探索到移出清單的項目。</span><span class="sxs-lookup"><span data-stu-id="2e12e-111">In addition, unlisted items will not be discoverable using the search bar.</span></span>
<span data-ttu-id="2e12e-112">只有指定項目的確切名稱與版本，才能下載移出清單的項目。</span><span class="sxs-lookup"><span data-stu-id="2e12e-112">The only way to download an unlisted item is to specify the exact name and version of the item.</span></span>
<span data-ttu-id="2e12e-113">因為如此，將項目移除清單不會中斷相依其上的其他模組或指令碼。</span><span class="sxs-lookup"><span data-stu-id="2e12e-113">Because of this, the unlisting of an item will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="2e12e-114">若要將您的項目移出清單，請前往項目詳細資料頁面，然後選取 [刪除項目]。</span><span class="sxs-lookup"><span data-stu-id="2e12e-114">To unlist your item, visit the item details page and select 'Delete Item'.</span></span> <span data-ttu-id="2e12e-115">取消選取 [列出] 核取方塊，然後按一下 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="2e12e-115">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="2e12e-116">**如何移除項目？**</span><span class="sxs-lookup"><span data-stu-id="2e12e-116">**How can I remove an item?**</span></span>

<span data-ttu-id="2e12e-117">如果您遇到必須刪除項目的情況，請連絡 PowerShell 資源庫系統管理員。</span><span class="sxs-lookup"><span data-stu-id="2e12e-117">If you experience a scenario where item deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="2e12e-118">合理的刪除案例為：</span><span class="sxs-lookup"><span data-stu-id="2e12e-118">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="2e12e-119">侵害著作權的問題。</span><span class="sxs-lookup"><span data-stu-id="2e12e-119">Issues of copyright infringement.</span></span>
- <span data-ttu-id="2e12e-120">項目包含可能有害的內容。</span><span class="sxs-lookup"><span data-stu-id="2e12e-120">Item contains potentially harmful content.</span></span>
- <span data-ttu-id="2e12e-121">項目包含敏感性資料。</span><span class="sxs-lookup"><span data-stu-id="2e12e-121">Item contains sensitive data.</span></span>

<span data-ttu-id="2e12e-122">若要提交「刪除項目要求」給 PowerShell 資源庫系統管理員，請前往項目的詳細資料頁面，然後選取 [連絡支援服務]。</span><span class="sxs-lookup"><span data-stu-id="2e12e-122">To submit a Delete Item Request to the PowerShell Gallery Administrators, visit your item's detail page and select Contact Support.</span></span>  


