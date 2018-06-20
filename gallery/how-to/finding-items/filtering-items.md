---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 篩選搜尋結果
ms.openlocfilehash: eafbc993a37eaee7413102ef9d669a6b07d6ff6e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188803"
---
# <a name="filtering-search-results"></a>篩選搜尋結果

[Items (項目) 索引標籤](https://www.powershellgallery.com/items) \(英文\) 會顯示 PowerShell 資源庫中的所有可用項目。

有數種方式可篩選、排序和搜尋項目。
若要查看特定項目的更多詳細資料，請按一下項目。

## <a name="filter-by"></a>篩選依據

[Filter By] \(篩選依據\) 之下的下拉式清單可讓使用者依據下列條件來篩選結果：
- Include Prerelease (包括發行前版本)
- Stable Only (僅限穩定)

如需「發行前版本」與「穩定版本」的相關資訊，請參閱 PowerShell 小組部落格中的 [PowerShellGet 與 PowerShell 資源庫新增了發行前版本的版本設定](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) \(英文\)。

下拉式清單之下的核取方塊可讓使用者依據下列條件來篩選結果：
- 項目類型
  - 模組
  - 指令碼
- 類別
  - Cmdlet
  - DSC 資源
  - 函式
  - 角色功能
  - 工作流程

若只要查看 PowerShell 資源庫中的模組，請選取 [Item Types] \(項目類型\) 中的 [Module] \(模組\)。
同樣地，若只要查看 PowerShell 資源庫中的指令碼，請選取 [Item Types] \(項目類型\) 中的 [Script] \(指令碼\)。

> [!NOTE]
> 篩選條件是內含的。
> 範例︰如果選取了 [Cmdlet] 或 [Function] \(函數\) 之一或兩者皆選取，將會出現同時包含 Cmdlet 和函數的項目。
> 如果未選取兩者，則不會顯示項目。
> 同樣地，如果選取所有類別，則只會顯示包含其中一種類別的項目。
> **不屬於所有這些類別的項目都不會出現。**

## <a name="sort-by"></a>排序依據

[Sort By] \(排序依據\) 下拉式清單可讓使用者依據下列條件來排序結果︰
- [Popularity] \(熱門程度\)：熱門程度取決於下載計數
- [A-Z]：依字母順序排序項目名稱
- [Recent] \(最近\)：依發行日期順序顯示項目

## <a name="search-box"></a>搜尋方塊

[搜尋] 方塊可讓使用者根據關鍵字來搜尋項目。
如需詳細資訊，請參閱[資源庫搜尋語法](search-syntax.md)。