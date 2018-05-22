---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 將項目從清單移除
ms.openlocfilehash: bdcceba0ba18ade6a1d0f94602fd8d0f64af8936
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
---
# <a name="unlisting-items"></a><span data-ttu-id="4bdf9-103">將項目從清單移除</span><span class="sxs-lookup"><span data-stu-id="4bdf9-103">Unlisting items</span></span>

<span data-ttu-id="4bdf9-104">**為什麼從 PowerShell 資源庫移除項目未公開為選項？**</span><span class="sxs-lookup"><span data-stu-id="4bdf9-104">**Why is removing an item from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="4bdf9-105">PowerShell 資源庫不支援使用者永久刪除項目。</span><span class="sxs-lookup"><span data-stu-id="4bdf9-105">The PowerShell Gallery does not support users permanently deleting their items.</span></span>
<span data-ttu-id="4bdf9-106">這可讓其他人對您的項目採取相依性，而不需要擔心日後可能中斷。</span><span class="sxs-lookup"><span data-stu-id="4bdf9-106">This enables others to take dependencies on your items without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="4bdf9-107">例如，如果 Pester 模組相依於 Azure 模組，但 Azure 模組已從資源庫移除，使用者就無法再使用 Pester 模組。</span><span class="sxs-lookup"><span data-stu-id="4bdf9-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="4bdf9-108">與其移除項目，您可以改為將其移出清單。</span><span class="sxs-lookup"><span data-stu-id="4bdf9-108">Instead of removing an item, however, you can unlist it instead.</span></span>

<span data-ttu-id="4bdf9-109">**在 PowerShell 資源庫將項目移出清單會如何？**</span><span class="sxs-lookup"><span data-stu-id="4bdf9-109">**What does unlisting an item on PowerShell Gallery do?**</span></span>

<span data-ttu-id="4bdf9-110">在 PowerShell 資源庫將模組或指令碼等項目移出清單，就會將其從 [項目] 索引標籤移除。此外，使用搜尋列將無法探索到移出清單的項目。</span><span class="sxs-lookup"><span data-stu-id="4bdf9-110">Unlisting an item such as module or script on PowerShell Gallery will remove it from the Items tab. In addition, unlisted items will not be discoverable using the search bar.</span></span>
<span data-ttu-id="4bdf9-111">只有指定項目的確切名稱與版本，才能下載移出清單的項目。</span><span class="sxs-lookup"><span data-stu-id="4bdf9-111">The only way to download an unlisted item is to specify the exact name and version of the item.</span></span>
<span data-ttu-id="4bdf9-112">因為如此，將項目移除清單不會中斷相依其上的其他模組或指令碼。</span><span class="sxs-lookup"><span data-stu-id="4bdf9-112">Because of this, the unlisting of an item will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="4bdf9-113">若要將您的項目移出清單，請前往項目詳細資料頁面，然後選取 [刪除項目]。</span><span class="sxs-lookup"><span data-stu-id="4bdf9-113">To unlist your item, visit the item details page and select 'Delete Item'.</span></span> <span data-ttu-id="4bdf9-114">取消選取 [列出] 核取方塊，然後按一下 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="4bdf9-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="4bdf9-115">**如何移除項目？**</span><span class="sxs-lookup"><span data-stu-id="4bdf9-115">**How can I remove an item?**</span></span>

<span data-ttu-id="4bdf9-116">如果您遇到必須刪除項目的情況，請連絡 PowerShell 資源庫系統管理員。</span><span class="sxs-lookup"><span data-stu-id="4bdf9-116">If you experience a scenario where item deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="4bdf9-117">合理的刪除案例為：</span><span class="sxs-lookup"><span data-stu-id="4bdf9-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="4bdf9-118">侵害著作權的問題。</span><span class="sxs-lookup"><span data-stu-id="4bdf9-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="4bdf9-119">項目包含可能有害的內容。</span><span class="sxs-lookup"><span data-stu-id="4bdf9-119">Item contains potentially harmful content.</span></span>
- <span data-ttu-id="4bdf9-120">項目包含敏感性資料。</span><span class="sxs-lookup"><span data-stu-id="4bdf9-120">Item contains sensitive data.</span></span>

<span data-ttu-id="4bdf9-121">若要提交「刪除項目要求」給 PowerShell 資源庫系統管理員，請前往項目的詳細資料頁面，然後選取 [連絡支援服務]。</span><span class="sxs-lookup"><span data-stu-id="4bdf9-121">To submit a Delete Item Request to the PowerShell Gallery Administrators, visit your item's detail page and select Contact Support.</span></span>