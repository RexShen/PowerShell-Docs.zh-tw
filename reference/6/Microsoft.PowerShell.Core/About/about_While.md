---
description: 描述您可以用來根據條件式測試結果執行命令區塊的語言語句。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_while?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_While
ms.openlocfilehash: 0adc435eeba6b07e1f16aec5dd1328ddd80c4612
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206808"
---
# <a name="about-while"></a>關於 While

## <a name="short-description"></a>簡短描述
描述您可以用來根據條件式測試結果執行命令區塊的語言語句。

## <a name="long-description"></a>詳細描述

While 語句 (也稱為 While 迴圈) 是一種語言結構，可用於建立在命令區塊中執行命令的迴圈（只要條件式測試評估為 true）。 While 語句比 For 語句更容易建立，因為其語法較不復雜。 此外，它比 Foreach 語句更有彈性，因為您在 While 語句中指定條件式測試來控制迴圈執行的次數。

以下顯示 While 語句語法：

```powershell
while (<condition>){<statement list>}
```

當您執行 While 語句時，PowerShell 會 `<condition>` 先評估語句的區段，然後再輸入 `<statement list>` 區段。 語句的條件部分會解析為 true 或 false。 只要條件維持為 true，PowerShell 就會重新運行 `<statement list>` 區段。

`<statement list>`語句的區段包含一或多個在每次輸入或重複迴圈時都會執行的命令。

例如，如果未建立 $val 變數，或是已建立 $val 變數，並將其初始化為0，則下列 While 語句會顯示數位1到3。

```powershell
while($val -ne 3)
{
    $val++
    Write-Host $val
}
```

在此範例中， ($val 的條件不等於 3) 在 $val \= 0、1、2時為 true。 每次執行迴圈時，$val 會使用 \+ \+ 一元遞增運算子 ($val) 遞增 1 \+ \+ 。 最後一次執行迴圈，$val \= 3。 當 $val 等於3時，條件陳述式會評估為 false，而且迴圈會結束。

若要在 PowerShell 命令提示字元中方便地寫入此命令，您可以透過下列方式輸入：

```powershell
while($val -ne 3){$val++; Write-Host $val}
```

請注意，分號會分隔第一個命令，此命令會將 $val 的值寫入主控台，而第二個命令會將1新增至 $val。

## <a name="see-also"></a>另請參閱

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Do](about_Do.md)

[about_Foreach](about_Foreach.md)

[about_For](about_For.md)

[about_Language_Keywords](about_Language_Keywords.md)
