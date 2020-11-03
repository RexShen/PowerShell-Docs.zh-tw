---
description: 描述您可以用來立即結束、、 `foreach` 、 `for` `while` `do` 、 `switch` 或 `trap` 語句的語句。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_break?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Break
ms.openlocfilehash: 8716f81163cfd34684c3ef7071f7827f2e9b5bcf
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207179"
---
# <a name="about-break"></a>關於 Break

## <a name="short-description"></a>簡短描述

描述您可以用來立即結束、、 `foreach` 、 `for` `while` `do` 、 `switch` 或 `trap` 語句的語句。

## <a name="long-description"></a>完整描述

`break`語句提供結束目前控制區塊的方法。
執行會在控制區塊之後的下一個語句繼續執行。 語句支援標籤。 標籤是您在腳本中指派給語句的名稱。

## <a name="using-break-in-loops"></a>在迴圈中使用 break

當 `break` 語句出現在迴圈中（例如，、、 `foreach` `for` 或迴圈）時 `do` `while` ，PowerShell 會立即結束迴圈。

`break`語句可以包含一個可讓您結束內嵌迴圈的標籤。 標籤可以在腳本中指定 any loop 關鍵字，例如 `foreach` 、 `for` 或 `while` 。

下列範例顯示如何使用 `break` 語句來結束 `for` 語句：

```powershell
for($i=1; $i -le 10; $i++) {
   Write-Host $i
   break
}
```

在此範例中， `break` `for` 當變數等於1時，語句會結束迴圈 `$i` 。 即使在 `for` 大於10的情況下，語句會評估為 **True** ，但在 `$i` 第一次執行迴圈時，PowerShell 會到達 break 語句 `for` 。

`break`在必須符合內部條件的迴圈中使用語句較為常見。 請考慮下列 `foreach` 語句範例：

```powershell
$i=0
$varB = 10,20,30,40
foreach ($val in $varB) {
  if ($val -eq 30) {
    break
  }
  $i++
}
Write-Host "30 was found in array index $i"
```

在此範例中，語句會逐一查看 `foreach` `$varB` 陣列。 `if`語句會評估為 False，這是迴圈執行的前兩倍，而變數 `$i` 會遞增1。 第三次執行迴圈時， `$i` 等於2， `$val` 變數等於30。 此時， `break` 語句會執行，而且迴圈會結束 `foreach` 。

### <a name="using-a-labeled-break-in-a-loop"></a>在迴圈中使用加上標籤的 break

`break`語句可以包含標籤。 如果您使用 `break` 關鍵字搭配標籤，則 PowerShell 會離開標示的迴圈，而不會結束目前的迴圈。
標籤是冒號，後面接著您指派的名稱。 標籤必須是語句中的第一個 token，其後必須接著迴圈關鍵字（例如） `while` 。

`break` 將執行移出已加上標籤的迴圈。 在內嵌迴圈中，它本身所使用的結果與 `break` 關鍵字不同。 此範例中有語句 `while` 與 `for` 語句：

```powershell
:myLabel while (<condition 1>) {
  for ($item in $items) {
    if (<condition 2>) {
      break myLabel
    }
    $item = $x   # A statement inside the For-loop
  }
}
$a = $c  # A statement after the labeled While-loop
```

如果條件2評估為 **True** ，則腳本的執行會跳至標記迴圈之後的語句。 在此範例中，會使用語句再次開始執行 `$a = $c` 。

您可以嵌套許多標示的迴圈，如下列範例所示。

```powershell
:red while (<condition1>) {
  :yellow while (<condition2>) {
    while (<condition3>) {
      if ($a) {break}
      if ($b) {break red}
      if ($c) {break yellow}
    }
    Write-Host "After innermost loop"
  }
  Write-Host "After yellow loop"
}
Write-Host "After red loop"
```

如果 `$b` 變數評估為 True，就會在標記為 "red" 的迴圈之後繼續執行腳本。 如果 `$c` 變數評估為 True，腳本控制項的執行會在標示為 "黃色" 的迴圈之後繼續執行。

如果 `$a` 變數評估為 True，則會在最內層迴圈之後繼續執行。 不需要標籤。

PowerShell 不會限制標籤可以繼續執行的程度。 標籤甚至可以跨腳本和函式呼叫界限傳遞控制。

## <a name="using-break-in-a-switch-statement"></a>在 switch 語句中使用 break

在 `switch` 結構中， `break` 會導致 PowerShell 結束程式 `switch` 代碼區塊。

`break`關鍵字是用來離開 `switch` 結構。 例如，下列語句會 `switch` 使用 `break` 語句來測試最特定的條件：

```powershell
$var = "word2"
switch -regex ($var) {
    "word2" {
      Write-Host "Exact" $_
      break
    }

    "word.*" {
      Write-Host "Match on the prefix" $_
      break
    }

    "w.*" {
      Write-Host "Match on at least the first letter" $_
      break
    }

    default {
      Write-Host "No match" $_
      break
    }
}
```

在此範例中， `$var` 會建立變數，並將其初始化為的字串值 `word2` 。 `switch`語句會使用 **Regex** 類別，先將變數值與詞彙比對 `word2` 。 因為變數值和語句中的第一個測試 `switch` 相符，所以語句中的第一個程式碼區塊會 `switch` 執行。

當 PowerShell 到達第一個 `break` 語句時，語句便會結束 `switch` 。 如果 `break` 從範例移除四個語句，則會符合全部四個條件。 `break`當符合最特定條件時，此範例會使用語句來顯示結果。

## <a name="using-break-in-a-trap-statement"></a>在 trap 語句中使用 break

如果在語句主體中執行的最後一個語句 `trap` 是 `break` ，則會隱藏 error 物件，並重新擲回例外狀況。

下列範例會建立使用語句所捕捉的 **DivideByZeroException** 例外狀況 `trap` 。

```powershell
function test {
  trap [DivideByZeroException] {
    Write-Host 'divide by zero trapped'
    break
  }

  $i = 3
  'Before loop'
  while ($true) {
     "1 / $i = " + (1 / $i--)
  }
  'After loop'
}
test
```

請注意，執行會在例外狀況時停止。 `After loop`永遠不會到達。
執行之後，就會重新擲回例外狀況 `trap` 。

```Output
Before loop
1 / 3 = 0.333333333333333
1 / 2 = 0.5
1 / 1 = 1
divide by zero trapped
Attempted to divide by zero.
At line:10 char:6
+      "1 / $i = " + (1 / $i--)
+      ~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [], ParentContainsErrorRecordException
    + FullyQualifiedErrorId : RuntimeException
```

## <a name="do-not-use-break-outside-of-a-loop-switch-or-trap"></a>請勿在迴圈、切換或陷阱之外使用 break

當在 `break` 直接支援 (迴圈、) 的結構之外使用時， `switch` `trap` PowerShell 會查閱封閉結構 _的呼叫堆疊_ 。 如果找不到封閉結構，則目前的運行空間會以安靜方式終止。

這表示不慎在封閉結構之外使用的函式和腳本， `break` 可能會不慎終止其 _呼叫_ 端。

在管線中使用（ `break` `break` 例如 `ForEach-Object` 腳本區塊），不只會結束管線，它可能會終止整個運行空間。

## <a name="see-also"></a>另請參閱

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Continue](about_Continue.md)

[about_For](about_For.md)

[about_Foreach](about_Foreach.md)

[about_Switch](about_Switch.md)

[about_Throw](about_Throw.md)

[about_Trap](about_Trap.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)

[about_While](about_While.md)
