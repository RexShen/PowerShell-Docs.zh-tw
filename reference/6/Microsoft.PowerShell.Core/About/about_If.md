---
description: 描述您可以用來根據一或多個條件式測試結果執行語句清單的語言命令。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_If
ms.openlocfilehash: 7f63b6f12743390608e0da72adb4098ce0583751
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207067"
---
# <a name="about-if"></a>關於

## <a name="short-description"></a>簡短描述
描述您可以用來根據一或多個條件式測試結果執行語句清單的語言命令。

## <a name="long-description"></a>詳細描述

`If`如果指定的條件式測試評估為 true，您可以使用語句來執行程式碼區塊。 如果所有先前的測試都評估為 false，您也可以指定要執行的一或多個其他條件式測試。 最後，如果沒有其他先前的條件式測試評估為 true，您可以指定另一個執行的程式碼區塊。

### <a name="syntax"></a>Syntax

下列範例顯示 `If` 語句語法：

```powershell
if (<test1>)
    {<statement list 1>}
[elseif (<test2>)
    {<statement list 2>}]
[else
    {<statement list 3>}]
```

當您執行 `If` 語句時，PowerShell 會將 `<test1>` 條件運算式評估為 true 或 false。 如果 `<test1>` 是 true，則會 `<statement list 1>` 執行，且 PowerShell 會結束 `If` 語句。 如果 `<test1>` 為 false，則 PowerShell 會評估條件陳述式所指定的條件 `<test2>` 。

如果 `<test2>` 是 true，則會 `<statement list 2>` 執行，且 PowerShell 會結束 `If` 語句。 如果 `<test1>` 和都 `<test2>` 評估為 false， `<statement list 3`> 程式碼區塊會執行，且 PowerShell 會結束 If 語句。

您可以使用多個 Elseif 語句來串連一系列的條件式測試。 因此，只有在所有先前的測試都為 false 時，才會執行每個測試。
如果您需要建立 `If` 包含許多 Elseif 語句的語句，請考慮改為使用 Switch 語句。

範例：

最簡單的 `If` 語句包含單一命令，且不包含任何 Elseif 語句或任何 Else 語句。 下列範例顯示語句的最簡單形式 `If` ：

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
```

在此範例中，如果 $a 變數大於2，條件就會評估為 true，而且會執行語句清單。 但是，如果 $a 小於或等於2，或不是現有的變數，語句就不 `If` 會顯示訊息。

藉由加入 Else 語句，當 $a 小於或等於2時，就會顯示訊息。 如下一個範例所示：

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
else {
    Write-Host ("The value $a is less than or equal to 2," +
        " is not created or is not initialized.")
}
```

若要進一步精簡此範例，您可以使用 Elseif 語句，在 $a 的值等於2時顯示訊息。 如下一個範例所示：

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
elseif ($a -eq 2) {
    Write-Host "The value $a is equal to 2."
}
else {
    Write-Host ("The value $a is less than 2 or" +
        " was not created or initialized.")
}
```

## <a name="see-also"></a>另請參閱

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Switch](about_Switch.md)
