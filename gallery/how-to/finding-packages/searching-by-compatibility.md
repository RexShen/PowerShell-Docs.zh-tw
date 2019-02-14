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
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>具有相容 PowerShell 版本或作業系統套件

從 5.1 版開始，PowerShell 提供代表各種功能集及平台相容性的不同版本。

## <a name="searching-by-powershell-edition"></a>搜尋依據 PowerShell 版本 
Powershell 的兩個版本是：
- **Desktop Edition:** 建置在.NET Framework，並提供與指令碼和模組在完整使用量的 Server Core 等的 Windows 和 Windows 桌面版本上執行的 PowerShell 版本的相容性。
- **Core Edition:** 建置在.NET Core，並提供與指令碼和模組的縮減版 Nano Server 等的 Windows 和 Windows IoT 上執行的 PowerShell 版本相容性。

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>PowerShell 資源庫可讓您篩選特定 PowerShell 版本相容的套件

如果封裝具有相容 pseditions 的指定，它們會列為 「 PowerShell 版本 」 的一部分在封裝的 [顯示] 頁面，也在封裝的結果。
您也可以搜尋相容的套件，使用 PowerShell。

![含有 PSEditions 的項目顯示網頁](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>搜尋資源庫 UI 中作用於 PowerShell Core 的套件

使用 Tags:"PSEdition_Desktop" 和 Tags:"PSEdition_Core" 篩選 PowerShell Gallery 上的套件。

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>使用 Tags:"PSEdition_Core" 搜尋與 PowerShell Core 版本相容的項目。

![與 Core PSEdition 相容之項目的搜尋結果](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>使用 Tags:"PSEdition_Desktop" 搜尋與 PowerShell Desktop 版本相容的項目。

![與 Desktop PSEdition 相容之項目的搜尋結果](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>搜尋以尋找使用 PowerShell 的相容版本的套件
您可以指定要篩選的 PowerShell 版本和作業系統的標記。 您使用`Find-Package`cmdlet 指定`-Tag`參數指定的版本和 （OS） 的目標。
就像這樣：

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>搜尋依作業系統 

由於 PowerShell Core 是適用於 Windows、 Linux 和 MacOS，資源庫中的封裝其設計可能會針對這些作業系統的任何組合。 在資源庫 UI 中使用下列 searchs 標籤尋找標記作業系統的套件：

- 標記:"Windows"
- 標籤: [Linux]
- 標籤："MacOS" 

您可以指定這些標記上`Find-Module`（和其他的 PowerShellGet 模組中的 cmdlet），如下所示：

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>搜尋多個的相容性

您可以尋找使用的語法具有多個的相容性的封裝： 

標籤：「 Compatibility1""Compatibility2 」 

例如，如果您要尋找我 Windows 和 Linux 電腦上執行的 PowerShell Core 相容性套件，使用搜尋標籤：

標籤："PSEdition_Core" "Windows" "Linux" 

若要使用 PowerShell 進行搜尋，您可以使用`Find-Module`（和 PowerShellGet 模組中的其他 cmdlet），如下所示：

```powewrshell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>撰寫和尋找與 PowerShell 版本相容之套件的詳細資訊

- [PSEditions 的模組](../../concepts/module-psedition-support.md)
- [搭配 PSEditions 的指令碼](../../concepts/script-psedition-support.md)
