---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: gallery,powershell,cmdlet,psgallery
title: 具有相容 PowerShell 版本或作業系統的套件
ms.openlocfilehash: 14038aa9b0453e1d06e6587e97da391b56297c75
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328439"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a><span data-ttu-id="14123-103">具有相容 PowerShell 版本或作業系統的套件</span><span class="sxs-lookup"><span data-stu-id="14123-103">Packages with compatible PowerShell Editions or Operating Systems</span></span>

<span data-ttu-id="14123-104">從 5.1 版開始，PowerShell 提供代表各種功能集及平台相容性的不同版本。</span><span class="sxs-lookup"><span data-stu-id="14123-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibilities.</span></span>

## <a name="searching-by-powershell-edition"></a><span data-ttu-id="14123-105">透過 PowerShell 版本搜尋</span><span class="sxs-lookup"><span data-stu-id="14123-105">Searching by PowerShell Edition</span></span>

<span data-ttu-id="14123-106">PowerShell 的兩個版本為：</span><span class="sxs-lookup"><span data-stu-id="14123-106">The two editions of PowerShell are:</span></span>
- <span data-ttu-id="14123-107">**Desktop Edition：** 建置在 .NET Framework 上，與在完整使用量的 Windows 版本 (如 Server Core 和 Windows Desktop) 上執行的 PowerShell 指令碼和模組目標版本相容相容。</span><span class="sxs-lookup"><span data-stu-id="14123-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="14123-108">**Core Edition：** 建置在 .NET Core 上，與在降低使用量的 Windows 版本 (如 Nano Server 和 Windows IoT) 上執行的 PowerShell 指令碼和模組目標版本相容。</span><span class="sxs-lookup"><span data-stu-id="14123-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="14123-109">PowerShell 資源庫可讓您篩選與特定 PowerShell 版本相容的套件</span><span class="sxs-lookup"><span data-stu-id="14123-109">PowerShell Gallery allows you to filter packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="14123-110">如果套件已指定相容的 PSEditions，則 PSEditions 會列為套件顯示頁面和套件結果中「PowerShell 版本」的一部分。</span><span class="sxs-lookup"><span data-stu-id="14123-110">If a package has compatible PSEditions specified, they are listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>
<span data-ttu-id="14123-111">您也可以使用 PowerShell 來搜尋相容的套件。</span><span class="sxs-lookup"><span data-stu-id="14123-111">You can also search for compatible packages using PowerShell.</span></span>

![含有 PSEditions 的項目顯示網頁](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a><span data-ttu-id="14123-113">在資源庫 UI 中搜尋可在 PowerShell Core 上運作的套件</span><span class="sxs-lookup"><span data-stu-id="14123-113">Search for packages in the gallery UI that work on PowerShell Core</span></span>

<span data-ttu-id="14123-114">使用 Tags:"PSEdition_Desktop" 和 Tags:"PSEdition_Core" 篩選 PowerShell Gallery 上的套件。</span><span class="sxs-lookup"><span data-stu-id="14123-114">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspsedition_core-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="14123-115">使用 Tags:"PSEdition_Core" 搜尋與 PowerShell Core 版本相容的項目。</span><span class="sxs-lookup"><span data-stu-id="14123-115">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![與 Core PSEdition 相容之項目的搜尋結果](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspsedition_desktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="14123-117">使用 Tags:"PSEdition_Desktop" 搜尋與 PowerShell Desktop 版本相容的項目。</span><span class="sxs-lookup"><span data-stu-id="14123-117">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![與 Desktop PSEdition 相容之項目的搜尋結果](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a><span data-ttu-id="14123-119">使用 PowerShell 來搜尋套件以尋找相容的版本</span><span class="sxs-lookup"><span data-stu-id="14123-119">Search for packages to find compatible editions using PowerShell</span></span>
<span data-ttu-id="14123-120">您可以指定標籤來篩選 PowerShell 版本和 OS。</span><span class="sxs-lookup"><span data-stu-id="14123-120">You can specify tags to filter for the PowerShell edition and OS.</span></span>
<span data-ttu-id="14123-121">您可以使用 `Find-Package` Cmdlet，指定 `-Tag` 參數來指定您瞄準的目標版本 (和 OS)。</span><span class="sxs-lookup"><span data-stu-id="14123-121">You use the `Find-Package` cmdlet specifying the `-Tag` parameter to specify the edition (and OS) you are targeting.</span></span>
<span data-ttu-id="14123-122">例如：</span><span class="sxs-lookup"><span data-stu-id="14123-122">Like this:</span></span>

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a><span data-ttu-id="14123-123">依作業系統搜尋</span><span class="sxs-lookup"><span data-stu-id="14123-123">Searching by Operating System</span></span>

<span data-ttu-id="14123-124">由於 PowerShell Core 可供 Windows、Linux 及 MacOS 使用，因此資源庫中套件可以針對這些作業系統的任何組合設計。</span><span class="sxs-lookup"><span data-stu-id="14123-124">Since PowerShell Core is available for Windows, Linux, and MacOS, packages in the Gallery may be designed for any combination of these operating systems.</span></span> <span data-ttu-id="14123-125">在資源庫 UI 中，使用下列搜尋標籤來尋找已由作業系統標記的套件：</span><span class="sxs-lookup"><span data-stu-id="14123-125">In the gallery UI use the following searchs tags to find packages tagged by operating system:</span></span>

- <span data-ttu-id="14123-126">標籤："Windows"</span><span class="sxs-lookup"><span data-stu-id="14123-126">Tags: "Windows"</span></span>
- <span data-ttu-id="14123-127">標籤："Linux"</span><span class="sxs-lookup"><span data-stu-id="14123-127">Tags: "Linux"</span></span>
- <span data-ttu-id="14123-128">標籤："MacOS"</span><span class="sxs-lookup"><span data-stu-id="14123-128">Tags: "MacOS"</span></span>

<span data-ttu-id="14123-129">您可以在 `Find-Module` (以及其他 PowerShellGet 模組中的 Cmdlet) 上指定這些標籤，例如：</span><span class="sxs-lookup"><span data-stu-id="14123-129">You can specify these tags on `Find-Module` (and other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a><span data-ttu-id="14123-130">搜尋多個相容性</span><span class="sxs-lookup"><span data-stu-id="14123-130">Searching for Multiple Compatibilities</span></span>

<span data-ttu-id="14123-131">您可以使用此語法，尋找具有多個相容性的套件：</span><span class="sxs-lookup"><span data-stu-id="14123-131">You can look for a package that has multiple compatibilities by using the syntax:</span></span>

<span data-ttu-id="14123-132">標籤："Compatibility1" "Compatibility2"</span><span class="sxs-lookup"><span data-stu-id="14123-132">Tags: "Compatibility1" "Compatibility2"</span></span>

<span data-ttu-id="14123-133">例如，若您要尋找具備 PowerShell Core 相容性且在我的 Windows 和 Linux 電腦上執行的套件，請使用搜尋標籤：</span><span class="sxs-lookup"><span data-stu-id="14123-133">For example, if you are looking for a package with PowerShell Core Compatibility that runs on both my Windows and Linux machines, use the search tags:</span></span>

<span data-ttu-id="14123-134">標籤："PSEdition_Core" "Windows" "Linux"</span><span class="sxs-lookup"><span data-stu-id="14123-134">Tags: "PSEdition_Core" "Windows" "Linux"</span></span>

<span data-ttu-id="14123-135">若要使用 PowerShell 搜尋，您可以使用 `Find-Module` (以及 PowerShellGet 模組中的其他 Cmdlet)，例如：</span><span class="sxs-lookup"><span data-stu-id="14123-135">To search using PowerShell, you can use the `Find-Module` (and the other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="14123-136">撰寫和尋找與 PowerShell 版本相容之套件的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="14123-136">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="14123-137">PSEditions 的模組</span><span class="sxs-lookup"><span data-stu-id="14123-137">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="14123-138">搭配 PSEditions 的指令碼</span><span class="sxs-lookup"><span data-stu-id="14123-138">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
