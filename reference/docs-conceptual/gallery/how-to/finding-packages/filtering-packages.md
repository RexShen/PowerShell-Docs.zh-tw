---
ms.date: 06/12/2017
title: 篩選搜尋結果
description: 此文章描述用來篩選 PowerShell 資源庫內容的使用者介面。
ms.openlocfilehash: cc375f3ddb35c95ed134776500bd326bc3db6b1a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661409"
---
# <a name="filtering-search-results"></a>篩選搜尋結果

[套件索引標籤](https://www.powershellgallery.com/packages) \(英文\) 會顯示 PowerShell 資源庫中的所有可用套件。

有數種方式可篩選、排序和搜尋套件。 若要查看特定套件的更多詳細資料，請按一下 [套件]。

## <a name="filter-by"></a>篩選依據

[Filter By] \(篩選依據\) 之下的下拉式清單可讓使用者依據下列條件來篩選結果：

- Include Prerelease (包括發行前版本)
- Stable Only (僅限穩定)

如需「發行前版本」與「穩定版本」的相關資訊，請參閱 PowerShell 小組部落格中的 [PowerShellGet 與 PowerShell 資源庫新增了發行前版本的版本設定](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) \(英文\)。

下拉式清單之下的核取方塊可讓使用者依據下列條件來篩選結果：

- 套件類型
  - 模組
  - 指令碼
- 類別
  - Cmdlet
  - DSC 資源
  - 函式
  - 角色功能
  - 工作流程

若只要查看 PowerShell 資源庫中的模組，請選取 [套件類型] 中的 [模組]。 同樣地，若只要查看 PowerShell 資源庫中的指令碼，請選取 [套件類型] 中的 [指令碼]。

> [!NOTE]
> 篩選條件是內含的。 範例：若已核取 [Cmdlet] 或 [函式] (或兩者)，將會顯示同時包含 Cmdlet 和函式的套件。 如果未選取兩者，則不會顯示套件。 同樣地，如果選取所有類別，則只會顯示包含其中一種類別的套件。 **不屬於所有這些類別的套件都不會出現。**

## <a name="sort-by"></a>排序依據

[Sort By] \(排序依據\) 下拉式清單可讓使用者依據下列條件來排序結果︰

- [Popularity] \(熱門程度\)：熱門程度取決於下載計數
- A-Z：依字母順序排序套件名稱
- 最近：依發行日期順序顯示套件

## <a name="search-box"></a>搜尋方塊

[搜尋] 方塊可讓使用者根據關鍵字來搜尋套件。
如需詳細資訊，請參閱[資源庫搜尋語法](search-syntax.md)。
