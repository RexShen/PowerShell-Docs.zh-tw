---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 刪除套件
ms.openlocfilehash: 6bfb43b95e51d38bd606198cb8d2d9af0aa0be1e
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71327929"
---
# <a name="deleting-packages"></a><span data-ttu-id="1d5f5-103">刪除套件</span><span class="sxs-lookup"><span data-stu-id="1d5f5-103">Deleting Packages</span></span>

<span data-ttu-id="1d5f5-104">PowerShell 資源庫不支援永久刪除套件，因為這樣會中斷任何仰賴該套件維持可用的人員。</span><span class="sxs-lookup"><span data-stu-id="1d5f5-104">The PowerShell Gallery does not support permanent deletion of packages, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="1d5f5-105">相反地，PowerShell 資源庫支援將套件「取消列出」，該操作可於網站上的套件管理頁面中完成。</span><span class="sxs-lookup"><span data-stu-id="1d5f5-105">Instead, the PowerShell Gallery supports a way to 'unlist' a package, which can be done in the package management page on the web site.</span></span>
<span data-ttu-id="1d5f5-106">將套件取消列出後，在 PowerShell 資源庫上瀏覽及使用 PowerShellGet 命令時，該套件都不會在搜尋及任何套件列表中顯示。</span><span class="sxs-lookup"><span data-stu-id="1d5f5-106">When a package is unlisted, it no longer shows up in search and in any package listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span>
<span data-ttu-id="1d5f5-107">不過，該項目仍可透過指定其確切版本維持可供下載，其中確切版本可允許自動化的指令碼繼續運作。</span><span class="sxs-lookup"><span data-stu-id="1d5f5-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="1d5f5-108">如果您遇到例外狀況，且認為必須刪除您的其中一個套件時，PowerShell 資源庫小組可以手動處理此狀況。</span><span class="sxs-lookup"><span data-stu-id="1d5f5-108">If you run into an exceptional situation where you think one of your packages must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span>
<span data-ttu-id="1d5f5-109">例如，若發生著作權侵權問題，或是可能有害的內容，即有充分的理由可將其刪除。</span><span class="sxs-lookup"><span data-stu-id="1d5f5-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span>
<span data-ttu-id="1d5f5-110">在該種情況下，您應透過 [PowerShell 資源庫](https://www.PowerShellGallery.com) \(英文\) 提交支援要求。</span><span class="sxs-lookup"><span data-stu-id="1d5f5-110">You should submit a support request through [PowerShell Gallery](https://www.PowerShellGallery.com) in that case.</span></span>
