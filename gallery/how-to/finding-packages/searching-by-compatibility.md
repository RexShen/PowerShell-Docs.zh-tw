---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: gallery,powershell,cmdlet,psgallery
title: 具有相容 PowerShell 版本或作業系統套件
ms.openlocfilehash: 8230866561d3021379a48cc2c83fb4104a4058c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676909"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a><span data-ttu-id="27c87-103">具有相容 PowerShell 版本或作業系統套件</span><span class="sxs-lookup"><span data-stu-id="27c87-103">Packages with compatible PowerShell Editions or Operating Systems</span></span>

<span data-ttu-id="27c87-104">從 5.1 版開始，PowerShell 提供代表各種功能集及平台相容性的不同版本。</span><span class="sxs-lookup"><span data-stu-id="27c87-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibilities.</span></span>

## <a name="searching-by-powershell-edition"></a><span data-ttu-id="27c87-105">搜尋依據 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="27c87-105">Searching by PowerShell Edition</span></span> 
<span data-ttu-id="27c87-106">Powershell 的兩個版本是：</span><span class="sxs-lookup"><span data-stu-id="27c87-106">The two editions of Powershell are:</span></span>
- <span data-ttu-id="27c87-107">**Desktop Edition:** 建置在.NET Framework，並提供與指令碼和模組在完整使用量的 Server Core 等的 Windows 和 Windows 桌面版本上執行的 PowerShell 版本的相容性。</span><span class="sxs-lookup"><span data-stu-id="27c87-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="27c87-108">**Core Edition:** 建置在.NET Core，並提供與指令碼和模組的縮減版 Nano Server 等的 Windows 和 Windows IoT 上執行的 PowerShell 版本相容性。</span><span class="sxs-lookup"><span data-stu-id="27c87-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="27c87-109">PowerShell 資源庫可讓您篩選特定 PowerShell 版本相容的套件</span><span class="sxs-lookup"><span data-stu-id="27c87-109">PowerShell Gallery allows you to filter packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="27c87-110">如果封裝具有相容 pseditions 的指定，它們會列為 「 PowerShell 版本 」 的一部分在封裝的 [顯示] 頁面，也在封裝的結果。</span><span class="sxs-lookup"><span data-stu-id="27c87-110">If a package has compatible PSEditions specified, they are listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>
<span data-ttu-id="27c87-111">您也可以搜尋相容的套件，使用 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="27c87-111">You can also search for compatible packages using PowerShell.</span></span>

![含有 PSEditions 的項目顯示網頁](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a><span data-ttu-id="27c87-113">搜尋資源庫 UI 中作用於 PowerShell Core 的套件</span><span class="sxs-lookup"><span data-stu-id="27c87-113">Search for packages in the gallery UI that work on PowerShell Core</span></span>

<span data-ttu-id="27c87-114">使用 Tags:"PSEdition_Desktop" 和 Tags:"PSEdition_Core" 篩選 PowerShell Gallery 上的套件。</span><span class="sxs-lookup"><span data-stu-id="27c87-114">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="27c87-115">使用 Tags:"PSEdition_Core" 搜尋與 PowerShell Core 版本相容的項目。</span><span class="sxs-lookup"><span data-stu-id="27c87-115">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![與 Core PSEdition 相容之項目的搜尋結果](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="27c87-117">使用 Tags:"PSEdition_Desktop" 搜尋與 PowerShell Desktop 版本相容的項目。</span><span class="sxs-lookup"><span data-stu-id="27c87-117">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![與 Desktop PSEdition 相容之項目的搜尋結果](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a><span data-ttu-id="27c87-119">搜尋以尋找使用 PowerShell 的相容版本的套件</span><span class="sxs-lookup"><span data-stu-id="27c87-119">Search for packages to find compatible editions using PowerShell</span></span>
<span data-ttu-id="27c87-120">您可以指定要篩選的 PowerShell 版本和作業系統的標記。</span><span class="sxs-lookup"><span data-stu-id="27c87-120">You can specify tags to filter for the PowerShell edition and OS.</span></span> <span data-ttu-id="27c87-121">您使用`Find-Package`cmdlet 指定`-Tag`參數指定的版本和 （OS） 的目標。</span><span class="sxs-lookup"><span data-stu-id="27c87-121">You use the `Find-Package` cmdlet specifying the `-Tag` parameter to specify the edition (and OS) you are targeting.</span></span>
<span data-ttu-id="27c87-122">就像這樣：</span><span class="sxs-lookup"><span data-stu-id="27c87-122">Like this:</span></span>

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a><span data-ttu-id="27c87-123">搜尋依作業系統</span><span class="sxs-lookup"><span data-stu-id="27c87-123">Searching by Operating System</span></span> 

<span data-ttu-id="27c87-124">由於 PowerShell Core 是適用於 Windows、 Linux 和 MacOS，資源庫中的封裝其設計可能會針對這些作業系統的任何組合。</span><span class="sxs-lookup"><span data-stu-id="27c87-124">Since PowerShell Core is available for Windows, Linux, and MacOS, packages in the Gallery may be designed for any combination of these operating systems.</span></span> <span data-ttu-id="27c87-125">在資源庫 UI 中使用下列 searchs 標籤尋找標記作業系統的套件：</span><span class="sxs-lookup"><span data-stu-id="27c87-125">In the gallery UI use the following searchs tags to find packages tagged by operating system:</span></span>

- <span data-ttu-id="27c87-126">標記:"Windows"</span><span class="sxs-lookup"><span data-stu-id="27c87-126">Tags: "Windows"</span></span>
- <span data-ttu-id="27c87-127">標籤: [Linux]</span><span class="sxs-lookup"><span data-stu-id="27c87-127">Tags: "Linux"</span></span>
- <span data-ttu-id="27c87-128">標籤："MacOS"</span><span class="sxs-lookup"><span data-stu-id="27c87-128">Tags: "MacOS"</span></span> 

<span data-ttu-id="27c87-129">您可以指定這些標記上`Find-Module`（和其他的 PowerShellGet 模組中的 cmdlet），如下所示：</span><span class="sxs-lookup"><span data-stu-id="27c87-129">You can specify these tags on `Find-Module` (and other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a><span data-ttu-id="27c87-130">搜尋多個的相容性</span><span class="sxs-lookup"><span data-stu-id="27c87-130">Searching for Multiple Compatibilities</span></span>

<span data-ttu-id="27c87-131">您可以尋找使用的語法具有多個的相容性的封裝：</span><span class="sxs-lookup"><span data-stu-id="27c87-131">You can look for a package that has multiple compatibilities by using the syntax:</span></span> 

<span data-ttu-id="27c87-132">標籤：「 Compatibility1""Compatibility2 」</span><span class="sxs-lookup"><span data-stu-id="27c87-132">Tags: "Compatibility1" "Compatibility2"</span></span> 

<span data-ttu-id="27c87-133">例如，如果您要尋找我 Windows 和 Linux 電腦上執行的 PowerShell Core 相容性套件，使用搜尋標籤：</span><span class="sxs-lookup"><span data-stu-id="27c87-133">For example, if you are looking for a package with PowerShell Core Compatibility that runs on both my Windows and Linux machines, use the search tags:</span></span>

<span data-ttu-id="27c87-134">標籤："PSEdition_Core" "Windows" "Linux"</span><span class="sxs-lookup"><span data-stu-id="27c87-134">Tags: "PSEdition_Core" "Windows" "Linux"</span></span> 

<span data-ttu-id="27c87-135">若要使用 PowerShell 進行搜尋，您可以使用`Find-Module`（和 PowerShellGet 模組中的其他 cmdlet），如下所示：</span><span class="sxs-lookup"><span data-stu-id="27c87-135">To search using PowerShell, you can use the `Find-Module` (and the other cmdlets in the PowerShellGet module), like this:</span></span>

```powewrshell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="27c87-136">撰寫和尋找與 PowerShell 版本相容之套件的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="27c87-136">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="27c87-137">PSEditions 的模組</span><span class="sxs-lookup"><span data-stu-id="27c87-137">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="27c87-138">搭配 PSEditions 的指令碼</span><span class="sxs-lookup"><span data-stu-id="27c87-138">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
