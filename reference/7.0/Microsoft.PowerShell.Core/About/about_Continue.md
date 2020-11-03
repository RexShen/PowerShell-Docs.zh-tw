---
description: 描述語句如何 `continue` 立即將程式流程傳回至程式迴圈、 `switch` 語句或語句的頂端 `trap` 。
keywords: powershell,cmdlet
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_continue?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Continue
ms.openlocfilehash: 4d76212307d79adf1292dd9a788772fdd94e5ff4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206655"
---
# <a name="about-continue"></a>關於繼續

## <a name="short-description"></a>簡短描述

描述語句如何 `continue` 立即將程式流程傳回至程式迴圈、 `switch` 語句或語句的頂端 `trap` 。

## <a name="long-description"></a>完整描述

`continue`語句會提供一種方式來結束目前的控制區塊，但會繼續執行，而不是完全結束。 語句支援標籤。
標籤是您在腳本中指派給語句的名稱。

## <a name="using-continue-in-loops"></a>在迴圈中使用 continue

未標記的 `continue` 語句會立即將程式流程傳回至由 `for` 、 `foreach` 、 `do` 或語句所控制之最內層迴圈的頂端 `while` 。 迴圈的目前反覆運算會終止，而迴圈會繼續進行下一個反復專案。

在下列範例中， `while` 如果變數等於5，程式流程會返回迴圈的頂端 `$ctr` 。 因此，會顯示1到10之間的所有數位，但5：

```powershell
while ($ctr -lt 10)
{
    $ctr += 1
    if ($ctr -eq 5)
    {
        continue
    }

    Write-Host -Object $ctr
}
```

使用迴圈時 `for` ，會在 `<Repeat>` 語句之後繼續執行，然後進行 `<Condition>` 測試。 在下列範例中，不會發生無限迴圈，因為遞減 `$i` 會出現在關鍵字之後 `continue` 。

```powershell
#   <Init>  <Condition> <Repeat>
for ($i = 0; $i -lt 10; $i++)
{
    Write-Host -Object $i
    if ($i -eq 5)
    {
        continue
        # Will not result in an infinite loop.
        $i--
    }
}
```

### <a name="using-a-labeled-continue-in-a-loop"></a>在迴圈中使用加上標籤的 continue

加上標籤的 `continue` 語句會終止反覆運算的執行，並將控制權轉移至目標的封入反復專案或 `switch` 語句標籤。

在下列範例中， `for` 當是 True 時，最內層會終止， `$condition` 而反復專案會在第二個 **True** `for` 迴圈中繼續 `labelB` 。

```powershell
:labelA for ($i = 1; $i -le 10; $i++) {
    :labelB for ($j = 1; $j -le 10; $j++) {
        :labelC for ($k = 1; $k -le 10; $k++) {
            if ($condition) {
                continue labelB
            } else {
                $condition = Update-Condition
            }
        }
    }
}
```

## <a name="using-continue-in-a-switch-statement"></a>在 switch 語句中使用 continue

中未標記的 `continue` 語句會 `switch` 終止目前反覆運算的 `switch` 執行，並將控制權轉移至的頂端， `switch` 以取得下一個輸入專案。

當有單一輸入專案結束 `continue` 整個 `switch` 語句時。
當 `switch` 輸入為集合時，會 `switch` 測試集合中的每個元素。 會結束 `continue` 目前的反復專案，並 `switch` 繼續下一個元素。

```powershell
switch (1,2,3) {
  2 { continue }  # moves on to the next element, 3
  default { $_ }
}
```

```Output
1
3
```

## <a name="using-continue-in-a-trap-statement"></a>在 trap 語句中使用 continue

如果在主體中執行的最後一個語句 `trap` 是 `continue` ，則會以無訊息方式忽略陷阱的錯誤，並繼續執行緊接在引發的語句後面的語句 `trap` 。

## <a name="do-not-use-continue-outside-of-a-loop-switch-or-trap"></a>請勿在迴圈、切換或陷阱之外使用 continue

當在 `continue` 直接支援 (迴圈、) 的結構之外使用時， `switch` `trap` PowerShell 會查閱封閉結構 _的呼叫堆疊_ 。 如果找不到封閉結構，則目前的運行空間會以安靜方式終止。

這表示不慎在封閉結構之外使用的函式和腳本 `continue` ，可能會不慎終止其 _呼叫_ 端。

在管線中使用（ `continue` 例如 `ForEach-Object` 腳本區塊），不只會結束管線，tt 可能會終止整個運行空間。

## <a name="see-also"></a>另請參閱

[about_Break](about_Break.md)

[about_For](about_For.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Throw](about_Throw.md)

[about_Trap](about_Trap.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)
