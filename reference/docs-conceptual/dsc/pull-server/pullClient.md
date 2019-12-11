---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 設定 DSC 提取用戶端
ms.openlocfilehash: 54c68ac26e5388260e252ce01418170e26ddecde
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71955165"
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="e6350-103">設定 DSC 提取用戶端</span><span class="sxs-lookup"><span data-stu-id="e6350-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="e6350-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e6350-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e6350-105">提取伺服器 (Windows 功能「DSC 服務」  ) 是支援的 Windows Server 元件，但未計劃提供新特性或功能。</span><span class="sxs-lookup"><span data-stu-id="e6350-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="e6350-106">建議開始將受控用戶端轉換為 [Azure 自動化 DSC](/azure/automation/automation-dsc-getting-started) (包括 Windows Server 上提取伺服器以外的功能)，或[此處](pullserver.md#community-solutions-for-pull-service)列出的其中一個社群解決方案。</span><span class="sxs-lookup"><span data-stu-id="e6350-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="e6350-107">必須告知每個目標節點使用提取模式和指定的 URL 或檔案位置，它可從中連絡提取伺服器以取得設定和資源，以及傳送報表資料。</span><span class="sxs-lookup"><span data-stu-id="e6350-107">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="e6350-108">下列主題說明如何設定提取用戶端：</span><span class="sxs-lookup"><span data-stu-id="e6350-108">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="e6350-109">使用設定名稱設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="e6350-109">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="e6350-110">使用設定識別碼設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="e6350-110">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> [!NOTE]
> <span data-ttu-id="e6350-111">這些主題適用於 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="e6350-111">These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="e6350-112">若要設定 PowerShell 4.0 中的提取用戶端，請參閱[使用 PowerShell 4.0 中的設定識別碼設定提取用戶端](pullClientConfigID4.md)。</span><span class="sxs-lookup"><span data-stu-id="e6350-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>