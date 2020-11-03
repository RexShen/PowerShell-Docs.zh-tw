---
description: 描述如何建立和使用參考型別變數。 您可以使用參考型別變數來允許函數變更傳遞給它的變數值。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/24/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_ref?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Ref
ms.openlocfilehash: fefc0f002db0b9591b2d23e148db381f7413871f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206948"
---
# <a name="about-ref"></a>關於參考

## <a name="short-description"></a>簡短描述
描述如何建立和使用參考型別變數。 您可以使用參考型別變數來允許函數變更傳遞給它的變數值。

## <a name="long-description"></a>完整描述

您可以透過傳 *址方式* 或 *依值* 傳遞變數給函數。

當您以傳 *值方式* 傳遞變數時，會傳遞資料的複本。

在下列範例中，函數會變更傳遞給它的變數值。 在 PowerShell 中，整數是實數值型別，因此會以傳值方式傳遞。
因此，的值會在函式的 `$var` 範圍之外保持不變。

```powershell
Function Test($data)
{
    $data = 3
}

$var = 10
Test -data $var
$var
```

```output
10
```

在下列範例中，會將包含的變數 `Hashtable` 傳遞至函式。 `Hashtable` 是物件類型，因此預設會以傳 *址方式* 傳遞至函式。

*以傳址方式* 傳遞變數時，函式可以變更資料，而且在函式執行之後仍會保存變更。

```powershell
Function Test($data)
{
    $data.Test = "New Text"
}

$var = @{}
Test -data $var
$var
```

```output
Name                           Value
----                           -----
Test                           New Text
```

函式會新增新的索引鍵/值組，以在函式的範圍之外保存。

### <a name="writing-functions-to-accept-reference-parameters"></a>撰寫函數以接受參考參數

無論傳遞的資料類型為何，您都可以撰寫函數的程式碼，以取得參數作為參考。 這需要您將參數類型指定為 `System.Management.Automation.PSReference` 或 `[ref]` 。

使用參考時，您必須使用 `Value` 型別的屬性 `System.Management.Automation.PSReference` 來存取您的資料。

```powershell
Function Test([ref]$data)
{
    $data.Value = 3
}
```

若要將變數傳遞給需要參考的參數，您必須輸入將變數轉換為參考。

> [!NOTE]
> 括弧和括弧都是必要的。

```powershell
$var = 10
Test -data ([ref]$var)
$var
```

```output
3
```

### <a name="passing-references-to-net-methods"></a>傳遞 .NET 方法的參考

某些 .NET 方法可能會要求您傳遞變數作為參考。 當方法的定義在 `in` 參數上使用關鍵字、或時， `out` `ref` 它需要參考。

```powershell
[int] | Get-Member -Static -Name TryParse
```

```output
Name     MemberType Definition
----     ---------- ----------
TryParse Method     static bool TryParse(string s, [ref] int result)
```

`TryParse`方法會嘗試將字串剖析為整數。 如果方法成功，它會傳回 `$true` ，而且結果會儲存在您以傳 **址方式** 傳遞的變數中。

```
PS> $number = 0
PS> [int]::TryParse("15", ([ref]$number))
True
PS> $number
15
```

### <a name="references-and-scopes"></a>參考和範圍

參考允許父範圍中的變數值在子範圍內變更。

```powershell
# Create a value type variable.
$i = 0
# Create a reference type variable.
$iRef = [ref]0
# Invoke a scriptblock to attempt to change both values.
&{$i++;$iRef.Value++}
# Output the results.
"`$i = $i;`$iRef = $($iRef.Value)"
```

```output
$i = 0;$iRef = 1
```

只有參考型別的變數已變更。

## <a name="see-also"></a>另請參閱

[about_Variables](about_Variables.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Functions](about_Functions.md)

[about_Script_Blocks](about_Script_Blocks.md)

[about_Scopes](about_scopes.md)
