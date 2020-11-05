---
ms.date: 12/11/2018
title: 具有相容 PowerShell 版本或作業系統的套件
description: 此文章描述如何根據與特定平台或版本的相容性來搜尋 PowerShell 資源庫。
ms.openlocfilehash: 9806c09c85febfd74bb69adf3d294fb4f559ff23
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661242"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>具有相容 PowerShell 版本或作業系統的套件

從 5.1 版開始，PowerShell 提供代表各種功能集及平台相容性的不同版本。

## <a name="searching-by-powershell-edition"></a>透過 PowerShell 版本搜尋

PowerShell 的兩個版本為：

- **Desktop Edition：** 建置在 .NET Framework 上，與在完整使用量的 Windows 版本 (如 Server Core 和 Windows Desktop) 上執行的 PowerShell 指令碼和模組目標版本相容相容。
- **Core Edition：** 建置在 .NET Core 上，與在降低使用量的 Windows 版本 (如 Nano Server 和 Windows IoT) 上執行的 PowerShell 指令碼和模組目標版本相容。

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>PowerShell 資源庫可讓您篩選與特定 PowerShell 版本相容的套件

如果套件已指定相容的 PSEditions，則 PSEditions 會列為套件顯示頁面和套件結果中「PowerShell 版本」的一部分。
您也可以使用 PowerShell 來搜尋相容的套件。

![含有 PSEditions 的項目顯示網頁](media/searching-by-compatibility/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>在資源庫 UI 中搜尋可在 PowerShell Core 上運作的套件

使用 Tags:"PSEdition_Desktop" 和 Tags:"PSEdition_Core" 篩選 PowerShell Gallery 上的套件。

### <a name="use-tagspsedition_core-to-search-items-compatible-with-powershell-core-edition"></a>使用 Tags:"PSEdition_Core" 來搜尋與 PowerShell Core 版本相容的項目

![與 Core PSEdition 相容之項目的搜尋結果](media/searching-by-compatibility/searchresultswithpseditions.PNG)

### <a name="use-tagspsedition_desktop-to-search-items-compatible-with-powershell-desktop-edition"></a>使用 Tags:"PSEdition_Desktop" 來搜尋與 PowerShell Desktop 版本相容的項目

![與 Desktop PSEdition 相容之項目的搜尋結果](media/searching-by-compatibility/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>使用 PowerShell 來搜尋套件以尋找相容的版本

您可以指定標籤來篩選 PowerShell 版本和 OS。 您可以使用 `Find-Package` Cmdlet，指定 `-Tag` 參數來指定您瞄準的目標版本 (和 OS)。 例如：

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>依作業系統搜尋

由於 PowerShell Core 可供 Windows、Linux 及 MacOS 使用，因此資源庫中套件可以針對這些作業系統的任何組合設計。 在資源庫 UI 中，使用下列搜尋標籤來尋找已由作業系統標記的套件：

- 標籤："Windows"
- 標籤："Linux"
- 標籤："MacOS"

您可以在 `Find-Module` (以及其他 PowerShellGet 模組中的 Cmdlet) 上指定這些標籤，例如：

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>搜尋多個相容性

您可以使用此語法，尋找具有多個相容性的套件：

標籤："Compatibility1" "Compatibility2"

例如，若您要尋找具備 PowerShell Core 相容性且在我的 Windows 和 Linux 電腦上執行的套件，請使用搜尋標籤：

標籤："PSEdition_Core" "Windows" "Linux"

若要使用 PowerShell 搜尋，您可以使用 `Find-Module` (以及 PowerShellGet 模組中的其他 Cmdlet)，例如：

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>撰寫和尋找與 PowerShell 版本相容之套件的詳細資訊

- [PSEditions 的模組](../../concepts/module-psedition-support.md)
- [搭配 PSEditions 的指令碼](../../concepts/script-psedition-support.md)
