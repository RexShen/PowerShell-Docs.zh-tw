---
description: 結束目前的範圍，這可以是函式、指令碼或指令碼區塊。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_return?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Return
ms.openlocfilehash: 3b1900d2d2f17c78c0f935bf86400af37fc7d9ec
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206900"
---
# <a name="about-return"></a>關於 Return

## <a name="short-description"></a>簡短描述

結束目前的範圍，這可以是函式、指令碼或指令碼區塊。

## <a name="long-description"></a>完整描述

關鍵字會結束函式 `return` 、腳本或腳本區塊。 您可以使用它來結束特定點的範圍、傳回值，或指出已到達範圍的結尾。

熟悉 C 或 C 等語言的使用者， \# 可能會想要使用 `return` 關鍵字來讓範圍保持明確的邏輯。

在 PowerShell 中，即使沒有包含關鍵字的語句，每個語句的結果都會以輸出形式傳回 `return` 。 C 或 C 之類的語言 \# 只會傳回關鍵字所指定的值或值 `return` 。

> [!NOTE]
> 從 PowerShell 5.0 開始，PowerShell 使用正式語法來新增定義類別的語言。  在 PowerShell 類別的內容中，除了指定語句以外，方法的輸出不會有任何結果 `return` 。 您可以在 [about_Classes](about_Classes.md)中深入瞭解 PowerShell 類別。

### <a name="syntax"></a>Syntax

關鍵字的語法如下所示 `return` ：

```
return [<expression>]
```

`return`關鍵字可以單獨出現，也可以其後接著值或運算式，如下所示：

```powershell
return
return $a
return (2 + $a)
```

### <a name="examples"></a>範例

下列範例 `return` 會在符合條件時，使用關鍵字來結束特定點的函式。 奇數數位不會相乘，因為 `return` 語句會在語句執行之前結束。

```powershell
function MultiplyEven
{
    param($number)

    if ($number % 2) { return "$number is not even" }
    $number * 2
}

1..10 | ForEach-Object {MultiplyEven -Number $_}
```

```output
1 is not even
4
3 is not even
8
5 is not even
12
7 is not even
16
9 is not even
20
```

在 PowerShell 中，即使未使用關鍵字，也可以傳回值 `return` 。
會傳回每個語句的結果。 例如，下列語句會傳回變數的值 `$a` ：

```powershell
$a
return
```

下列語句也會傳回的值 `$a` ：

```powershell
return $a
```

下列範例包含一個語句，其目的是要讓使用者知道函式正在執行計算：

```powershell
function calculation {
    param ($value)

    "Please wait. Working on calculation..."
    $value += 73
    return $value
}

$a = calculation 14
```

「請稍候。 正在處理計算 ...」不顯示字串。 相反地，它會指派給 `$a` 變數，如下列範例所示：

```
PS> $a
Please wait. Working on calculation...
87
```

參考字串和計算結果都是由函式傳回並指派給 `$a` 變數。

如果您想要在函式內顯示訊息，從 PowerShell 5.0 開始，您可以使用此 `Information` 資料流程。 下列程式碼會使用 `Write-Information` Cmdlet 搭配 `InformationAction` **Continue** 來修正上述範例。

```powershell
function calculation {
    param ($value)

    Write-Information "Please wait. Working on calculation..." -InformationAction Continue
    $value += 73
    return $value
}

$a = calculation 14
```

```output
Please wait. Working on calculation...
C:\PS> $a
87
```

### <a name="return-values-and-the-pipeline"></a>傳回值和管線

當您從腳本區塊或函式傳回集合時，PowerShell 會自動展開成員，並透過管線一次傳遞一個。 這是因為 PowerShell 的一次性處理。 如需詳細資訊，請參閱 [about_pipelines](about_pipelines.md)。

下列會傳回數位陣列的範例函式說明這個概念。 函式的輸出會以管道傳送至 `Measure-Object` Cmdlet，以計算管線中的物件數目。

```powershell
function Test-Return
{
    $array = 1,2,3
    return $array
}
Test-Return | Measure-Object
```

```Output
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

若要強制腳本區塊或函數將集合以單一物件的形式傳回至管線，請使用下列兩種方法之一：

- 一元陣列運算式

  利用一元運算式，您可以將管線的傳回值以單一物件的形式傳送，如下列範例所示。

  ```powershell
  function Test-Return
  {
      $array = 1,2,3
      return (, $array)
  }
  Test-Return | Measure-Object
  ```

  ```Output
  Count    : 1
  Average  :
  Sum      :
  Maximum  :
  Minimum  :
  Property :
  ```

- `Write-Output` with **NoEnumerate** 參數。

  您也可以使用 `Write-Output` Cmdlet 搭配 **NoEnumerate** 參數。 下列範例會使用 `Measure-Object` Cmdlet 來計算從範例函式依關鍵字傳送至管線的物件 `return` 。

  ```powershell
  function Test-Return
  {
      $array = 1, 2, 3
      return Write-Output -NoEnumerate $array
  }

  Test-Return | Measure-Object
  ```

  ```Output
  Count    : 1
  Average  :
  Sum      :
  Maximum  :
  Minimum  :
  Property :
  ```

## <a name="see-also"></a>另請參閱

[about_Language_Keywords](about_Language_Keywords.md)

[about_Functions](about_Functions.md)

[about_Scopes](about_Scopes.md)

[about_Classes](about_Classes.md)

[Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)

[about_Script_Blocks](about_Script_Blocks.md)
