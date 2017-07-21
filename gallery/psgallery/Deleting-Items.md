---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: "刪除項目"
ms.openlocfilehash: 00452f9b6625a51e95f3f46dbd66291fa20e17ad
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="deleting-items"></a><span data-ttu-id="5cb43-103">刪除項目</span><span class="sxs-lookup"><span data-stu-id="5cb43-103">Deleting items</span></span>

<span data-ttu-id="5cb43-104">PowerShell 資源庫不支援永久刪除項目，因為這樣會中斷任何仰賴該項目維持可用的人員。</span><span class="sxs-lookup"><span data-stu-id="5cb43-104">The PowerShell Gallery does not support permanent deletion of items, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="5cb43-105">相反地，PowerShell 資源庫支援將項目「取消列出」，該操作可於網站上的項目管理頁面完成。</span><span class="sxs-lookup"><span data-stu-id="5cb43-105">Instead, the PowerShell Gallery supports a way to 'unlist' an item, which can be done in the item management page on the web site.</span></span> <span data-ttu-id="5cb43-106">將項目取消列出後，在 PowerShell 資源庫中及使用 PowerShellGet 命令時，該項目都不會在搜尋及任何項目列表中顯示。</span><span class="sxs-lookup"><span data-stu-id="5cb43-106">When an item is unlisted, it no longer shows up in search and in any item listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span> <span data-ttu-id="5cb43-107">不過，該項目仍可透過指定其確切版本維持可供下載，其中確切版本可允許自動化的指令碼繼續運作。</span><span class="sxs-lookup"><span data-stu-id="5cb43-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="5cb43-108">如果您遇到例外狀況，且認為您的其中一個項目必須刪除時，PowerShell 資源庫小組可以手動處理此狀況。</span><span class="sxs-lookup"><span data-stu-id="5cb43-108">If you run into an exceptional situation where you think one of your items must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span> <span data-ttu-id="5cb43-109">例如，若發生著作權侵權問題，或是可能有害的內容，即有充分的理由可將其刪除。</span><span class="sxs-lookup"><span data-stu-id="5cb43-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span> <span data-ttu-id="5cb43-110">在此類情況下，您應透過 [PowerShell 資源庫] (http://www.PowerShellGallery.com) 提交支援要求。</span><span class="sxs-lookup"><span data-stu-id="5cb43-110">You should submit a support request through [PowerShell Gallery] (http://www.PowerShellGallery.com) in that case.</span></span>

