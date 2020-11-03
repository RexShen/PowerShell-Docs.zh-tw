---
description: 執行一個或多個語句清單，受限於 While 或 Until 條件。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_do?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Do
ms.openlocfilehash: 9c5a7c561fde4d96401771870cf4e85d78591593
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208052"
---
# <a name="about-do"></a>關於

## <a name="short-description"></a>簡短描述

執行一個或多個語句清單，受限於 While 或 Until 條件。

## <a name="long-description"></a>詳細描述

Do 關鍵字適用于 While 關鍵字或 Until 關鍵字，以執行腳本區塊中的語句，受限於條件。 與相關 While 迴圈不同的是，Do 迴圈中的腳本區塊一律會至少執行一次。

While **迴圈是** 各種 While 迴圈。 在 **Do While** 迴圈中，此條件會在腳本區塊執行之後評估。 如同 While 迴圈一樣，只要條件評估為 true，就會重複執行腳本區塊。

就像 **While** 迴圈一樣，在評估條件之前， **Do Until** 迴圈一律會至少執行一次。 不過，腳本區塊只會在條件為 false 時執行。

*Continue* 和 *Break* 流程式控制制關鍵字可用於 **do While** 迴圈中，或在 **do Until** 迴圈中使用。

### <a name="syntax"></a>Syntax

以下顯示 **Do While** 語句的語法：

```powershell
do {<statement list>} while (<condition>)
```

以下顯示 **Do Until** 語句的語法：

```powershell
do {<statement list>} until (<condition>)
```

語句清單包含一或多個在每次輸入或重複迴圈時執行的語句。

語句的條件部分會解析為 true 或 false。

### <a name="example"></a>範例

下列 Do 語句範例會計算陣列中的專案，直到到達值為0的專案為止。

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } while ($x[$a] -ne 0)
C:\PS> $count
3
```

下列範例會使用 Until 關鍵字。 請注意，不等於運算子 (`-ne`) 會取代為等於運算子 (`-eq`) 。

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } until ($x[$a] -eq 0)
C:\PS> $count
3
```

下列範例會寫入陣列的所有值，並略過任何小於零的值。

```powershell
do {
  if ($x[$a] -lt 0) { continue }
  Write-Host $x[$a]
}
while (++$a -lt 10)
```

## <a name="see-also"></a>另請參閱

[about_While](about_While.md)

[about_Operators](about_Operators.md)

[about_Assignment_Operators](about_Assignment_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)
