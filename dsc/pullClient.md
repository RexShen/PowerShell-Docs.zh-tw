---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "設定 DSC 提取用戶端"
ms.openlocfilehash: 98a67b8d27eeb445bb70f75253ca31e12207d5bd
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="0e86f-103">設定 DSC 提取用戶端</span><span class="sxs-lookup"><span data-stu-id="0e86f-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="0e86f-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0e86f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="0e86f-105">必須告知每個目標節點使用提取模式和指定的 URL 或檔案位置，它可從中連絡提取伺服器以取得設定和資源，以及傳送報表資料。</span><span class="sxs-lookup"><span data-stu-id="0e86f-105">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>


<span data-ttu-id="0e86f-106">下列主題說明如何設定提取用戶端：</span><span class="sxs-lookup"><span data-stu-id="0e86f-106">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="0e86f-107">使用設定名稱設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="0e86f-107">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="0e86f-108">使用設定識別碼設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="0e86f-108">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="0e86f-109">**注意**：這些主題適用於 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="0e86f-109">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="0e86f-110">若要設定 PowerShell 4.0 中的提取用戶端，請參閱[使用 PowerShell 4.0 中的設定識別碼設定提取用戶端](pullClientConfigID4.md)。</span><span class="sxs-lookup"><span data-stu-id="0e86f-110">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>

