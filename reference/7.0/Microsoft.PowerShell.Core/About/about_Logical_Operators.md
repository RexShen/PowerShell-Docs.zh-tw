---
description: 描述 PowerShell 中連接語句的運算子。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logical_operators?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logical_Operators
ms.openlocfilehash: 1262ed0f5797d8dcb8cb4719cad69ac6b6a28d59
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207380"
---
# <a name="about_logical_operators"></a>about_Logical_Operators

## <a name="short-description"></a>簡短描述
描述 PowerShell 中連接語句的運算子。

## <a name="long-description"></a>詳細描述

PowerShell 邏輯運算子會連接運算式和語句，讓您可以使用單一運算式來測試多個條件。

例如，下列語句會使用 and 運算子和 or 運算子來連接三個條件陳述式。 只有當 $a 的值大於 $b 的值，且 $a 或 $b 小於時，此語句才會是 true。
20.

```powershell
($a -gt $b) -and (($a -lt 20) -or ($b -lt 20))
```

PowerShell 支援下列邏輯運算子。

|運算子|描述                        |範例                   |
|--------|-----------------------------------|--------------------------|
|`-and`  |邏輯 AND。 當兩者都為 TRUE        |`(1 -eq 1) -and (1 -eq 2)`|
|        |陳述為 TRUE。               |`False`                   |
|`-or`   |邏輯 OR。 若為 TRUE，則為 TRUE       |`(1 -eq 1) -or (1 -eq 2)` |
|        |語句為 TRUE。                 |`True`                    |
|`-xor`  |邏輯排除 OR。 若為 TRUE    |`(1 -eq 1) -xor (2 -eq 2)`|
|        |只有一個語句為 TRUE         |`False`                   |
|`-not`  |邏輯 not。 否定語句 |`-not (1 -eq 1)`          |
|        |如下所示。                      |`False`                   |
|`!`     |與 `-not` 相同                     |`!(1 -eq 1)`              |
|        |                                   |`False`                   |

 附註：

先前的範例也使用等於比較運算子 `-eq` 。 如需詳細資訊，請參閱 [about_Comparison_Operators](about_Comparison_Operators.md)。 這些範例也會使用整數的布林值。 整數0的值為 FALSE。 所有其他整數的值都是 TRUE。

邏輯運算子的語法如下所示：

```
<statement> {-AND | -OR | -XOR} <statement>
{! | -NOT} <statement>
```

使用邏輯運算子的語句會傳回布林值 (TRUE 或 FALSE) 值。

PowerShell 邏輯運算子只會評估判斷語句之真值所需的語句。 如果包含 and 運算子之語句中的左運算元為 FALSE，則不會評估右邊的運算元。
如果包含或語句之語句中的左運算元為 TRUE，則不會評估右邊的運算元。 如此一來，您就可以使用語句的相同方式來使用這些語句 `If` 。

## <a name="see-also"></a>另請參閱

[about_Operators](about_Operators.md)

[Compare-Object](xref:Microsoft.PowerShell.Utility.Compare-Object)

[about_Comparison_operators](about_Comparison_Operators.md)

[about_If](about_If.md)
