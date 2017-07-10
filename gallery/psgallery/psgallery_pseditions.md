---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_pseditions
ms.openlocfilehash: 6634da5c2dadee9c0c6470b3d3e8883e6d02160f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a id="items-with-compatible-powershell-editions" class="xliff"></a>
# 具有相容 PowerShell 版本的項目
從 5.1 版開始，PowerShell 提供代表各種功能集及平台相容性的不同版本。

- **Desktop Edition︰**建置在 .NET Framework 上，與在完整使用量的 Windows 版本 (如 Server Core 和 Windows Desktop) 上執行之 PowerShell 版本的指令碼和模組相容。
- **Core Edition︰**建置在 .NET Core 上，與在降低使用量的 Windows 版本 (如 Nano Server 和 Windows IoT) 上執行之 PowerShell 版本的指令碼和模組相容。

<a id="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions" class="xliff"></a>
## PowerShell Gallery 會擷取支援的 PSEditions 中繼資料，並可讓您篩選與特定 PowerShell 版本相容的項目。

如果項目已指定相容的 PSEditions，則 PSEditions 會列為項目顯示頁面和項目結果中「PowerShell 版本」的一部分。
![含有 PSEditions 的項目顯示網頁](Images/ItemDisplayPageWithPSEditions.PNG)

<a id="search-for-items-in-the-gallery-ui-which-works-on-powershellcore" class="xliff"></a>
## 搜尋組件庫 UI 中適用於 PowerShellCore 的項目
使用 Tags:"PSEdition_Desktop" 和 Tags:"PSEdition_Core" 篩選 PowerShell Gallery 上的項目。

<a id="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition" class="xliff"></a>
### 使用 Tags:"PSEdition_Core" 搜尋與 PowerShell Core 版本相容的項目。
![與 Core PSEdition 相容之項目的搜尋結果](Images/SearchResultsWithPSEditions.PNG)

<a id="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition" class="xliff"></a>
### 使用 Tags:"PSEdition_Desktop" 搜尋與 PowerShell Desktop 版本相容的項目。
![與 Desktop PSEdition 相容之項目的搜尋結果](Images/SearchResultsWithPSEdition_Desktop.PNG)

<a id="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions" class="xliff"></a>
## 撰寫和尋找與 PowerShell 版本相容之項目的詳細資訊
<a id="modules-with-pseditionspsgetmodulemodulewithpseditionsupportmd" class="xliff"></a>
### [PSEditions 的模組](../psget/module/modulewithpseditionsupport.md)
<a id="scripts-with-pseditionspsgetscriptscriptwithpseditionsupportmd" class="xliff"></a>
### [搭配 PSEditions 的指令碼](../psget/script/scriptwithpseditionsupport.md)

