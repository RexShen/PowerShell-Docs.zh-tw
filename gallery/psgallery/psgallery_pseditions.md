---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_pseditions
ms.openlocfilehash: 0b30c1da53832a6b74be7aa14ed9331b1e9fe643
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="items-with-compatible-powershell-editions"></a><span data-ttu-id="2cb24-103">具有相容 PowerShell 版本的項目</span><span class="sxs-lookup"><span data-stu-id="2cb24-103">Items with compatible PowerShell Editions</span></span>
<span data-ttu-id="2cb24-104">從 5.1 版開始，PowerShell 提供代表各種功能集及平台相容性的不同版本。</span><span class="sxs-lookup"><span data-stu-id="2cb24-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="2cb24-105">**Desktop Edition︰**建置在 .NET Framework 上，與在完整使用量的 Windows 版本 (如 Server Core 和 Windows Desktop) 上執行之 PowerShell 版本的指令碼和模組相容。</span><span class="sxs-lookup"><span data-stu-id="2cb24-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="2cb24-106">**Core Edition︰**建置在 .NET Core 上，與在降低使用量的 Windows 版本 (如 Nano Server 和 Windows IoT) 上執行之 PowerShell 版本的指令碼和模組相容。</span><span class="sxs-lookup"><span data-stu-id="2cb24-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions"></a><span data-ttu-id="2cb24-107">PowerShell Gallery 會擷取支援的 PSEditions 中繼資料，並可讓您篩選與特定 PowerShell 版本相容的項目。</span><span class="sxs-lookup"><span data-stu-id="2cb24-107">PowerShell Gallery extracts supported PSEditions metadata and allows you to filters the items compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="2cb24-108">如果項目已指定相容的 PSEditions，則 PSEditions 會列為項目顯示頁面和項目結果中「PowerShell 版本」的一部分。</span><span class="sxs-lookup"><span data-stu-id="2cb24-108">If an item has compatible PSEditions specified, they will be listed as part of 'PowerShell Editions' in the item display page and also in items results.</span></span>
<span data-ttu-id="2cb24-109">![含有 PSEditions 的項目顯示網頁](Images/ItemDisplayPageWithPSEditions.PNG)</span><span class="sxs-lookup"><span data-stu-id="2cb24-109">![Item display page with PSEditions](Images/ItemDisplayPageWithPSEditions.PNG)</span></span>

## <a name="search-for-items-in-the-gallery-ui-which-works-on-powershellcore"></a><span data-ttu-id="2cb24-110">搜尋組件庫 UI 中適用於 PowerShellCore 的項目</span><span class="sxs-lookup"><span data-stu-id="2cb24-110">Search for items in the gallery UI which works on PowerShellCore</span></span>
<span data-ttu-id="2cb24-111">使用 Tags:"PSEdition_Desktop" 和 Tags:"PSEdition_Core" 篩選 PowerShell Gallery 上的項目。</span><span class="sxs-lookup"><span data-stu-id="2cb24-111">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the items on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="2cb24-112">使用 Tags:"PSEdition_Core" 搜尋與 PowerShell Core 版本相容的項目。</span><span class="sxs-lookup"><span data-stu-id="2cb24-112">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>
![與 Core PSEdition 相容之項目的搜尋結果](Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="2cb24-114">使用 Tags:"PSEdition_Desktop" 搜尋與 PowerShell Desktop 版本相容的項目。</span><span class="sxs-lookup"><span data-stu-id="2cb24-114">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>
![與 Desktop PSEdition 相容之項目的搜尋結果](Images/SearchResultsWithPSEdition_Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions"></a><span data-ttu-id="2cb24-116">撰寫和尋找與 PowerShell 版本相容之項目的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="2cb24-116">More details on authoring and finding the items with compatible PowerShell Editions</span></span>
### <a name="modules-with-pseditionspsgetmodulemodulewithpseditionsupportmd"></a>[<span data-ttu-id="2cb24-117">PSEditions 的模組</span><span class="sxs-lookup"><span data-stu-id="2cb24-117">Modules with PSEditions</span></span>](../psget/module/modulewithpseditionsupport.md)
### <a name="scripts-with-pseditionspsgetscriptscriptwithpseditionsupportmd"></a>[<span data-ttu-id="2cb24-118">搭配 PSEditions 的指令碼</span><span class="sxs-lookup"><span data-stu-id="2cb24-118">Scripts with PSEditions</span></span>](../psget/script/scriptwithpseditionsupport.md)