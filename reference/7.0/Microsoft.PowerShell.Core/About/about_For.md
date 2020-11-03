---
description: 描述您可以用來根據條件式測試執行語句的語言命令。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 3/4/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_for?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_For
ms.openlocfilehash: 0cc86c5969519f4c60702fdc1aed0a86ce11e1a1
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208200"
---
# <a name="about-for"></a>關於

## <a name="short-description"></a>簡短描述
描述您可以用來根據條件式測試執行語句的語言命令。

## <a name="long-description"></a>完整描述

`For`語句 (也稱為 `For` 迴圈) 是一種語言結構，可讓您在指定的條件評估為時，用來建立在命令區塊中執行命令的迴圈 `$true` 。

迴圈的一般用法 `For` 是反覆運算值的陣列，並在這些值的子集上運作。 在大部分的情況下，如果您想要逐一查看陣列中的所有值，請考慮使用 `Foreach` 語句。

### <a name="syntax"></a>Syntax

以下顯示 `For` 語句語法。

```
for (<Init>; <Condition>; <Repeat>)
{
    <Statement list>
}
```

**Init** 預留位置代表在迴圈開始之前執行的一或多個命令。 您通常會使用語句的 **Init** 部分來建立和初始化具有起始值的變數。

然後，這個變數會是在語句下一個部分中測試條件的基礎 `For` 。

**條件** 預留位置代表 `For` 解析為 `$true` 或 `$false` **布林** 值之語句的部分。 PowerShell 會在每次執行迴圈時評估條件 `For` 。 如果語句是 `$true` ，則會執行命令區塊中的命令，並再次評估語句。 如果條件仍然是 `$true` ，則 **語句清單** 中的命令會再次執行。 迴圈會重複，直到條件變成為止 `$false` 。

**重複** 的預留位置代表一個或多個命令（以逗號分隔），這些命令會在每次迴圈重複時執行。 一般來說，這是用來修改在語句的 **條件** 部分內測試的變數。

**語句清單** 預留位置代表一組一或多個在每次輸入或重複迴圈時都會執行的命令。 **語句清單** 的內容會以大括弧括住。

### <a name="support-for-multiple-operations"></a>支援多項作業

**Init** 語句中的多個指派作業支援下列語法：

```powershell
# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}
```

在 **重複** 語句中，有多個指派作業支援下列語法：

```powershell
# Comma separated assignment expressions.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; ($i++), ($j++))
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $($i++;$j++))
{
    "`$i:$i"
    "`$j:$j"
}
```

> [!NOTE]
> 前置或後置遞增以外的作業可能無法用於所有語法。

針對多個 **條件** ，請使用邏輯運算子，如下列範例所示。

```powershell
for (($i = 0), ($j = 0); $i -lt 10 -and $j -lt 10; $i++,$j++)
{
    "`$i:$i"
    "`$j:$j"
}
```

如需詳細資訊，請參閱 [about_Logical_Operators](about_Logical_Operators.md)。

### <a name="examples"></a>範例

`For`語句至少需要圍繞 **Init** 、 **Condition** 和 **Repeat** 部分的括弧，以及語句的 **語句清單** 部分中以大括弧括住的命令。

請注意，即將推出的範例會刻意顯示語句之外的程式碼 `For` 。 在稍後的範例中，程式碼會整合到 `For` 語句中。

例如，下列 `For` 語句會持續顯示變數的值， `$i` 直到您按下 CTRL + C 以手動方式中斷命令為止。

```powershell
$i = 1
for (;;)
{
    Write-Host $i
}
```

您可以將其他命令加入至語句清單，讓的值在 `$i` 每次執行迴圈時遞增1，如下列範例所示。

```powershell
for (;;)
{
    $i++; Write-Host $i
}
```

在您按下 CTRL + C 來中斷命令之前，此語句會持續顯示變數的值， `$i` 因為每次執行迴圈時，它會遞增1。

`For`您可以改為使用語句的 **重複** 部分，而不是變更語句的語句清單部分中的變數值，如下所示 `For` 。

```powershell
$i=1
for (;;$i++)
{
    Write-Host $i
}
```

除非您按下 CTRL + C，否則這個語句仍會無限期地重複執行，直到您中斷命令為止。

您可以 `For` 使用 *條件* 來結束迴圈。 您可以使用語句的 **條件** 部分來放置條件 `For` 。 `For`當條件評估為時，迴圈就會終止 `$false` 。

在下列範例中， `For` 迴圈會在的值 `$i` 小於或等於10時執行。

```powershell
$i=1
for(;$i -le 10;$i++)
{
    Write-Host $i
}
```

`For`您可以 `For` 使用語句的 **Init** 部分，在迴圈內執行這項工作，而不是在語句之外建立和初始化變數 `For` 。

```powershell
for($i=1; $i -le 10; $i++){Write-Host $i}
```

您可以使用換行字元（而不是分號）來分隔語句的 **Init** 、 **Condition** 和 **Repeat** 部分 `For` 。 下列範例顯示 `For` 使用這個替代語法的。

```powershell
for ($i = 0
  $i -lt 10
  $i++){
  $i
}
```

這種替代形式的 `For` 語句適用于 powershell 腳本檔案和 powershell 命令提示字元。 但是， `For` 當您在命令提示字元中輸入互動式命令時，以分號使用語句語法會比較容易。

`For`迴圈比迴圈更有彈性， `Foreach` 因為它可讓您使用模式來遞增陣列或集合中的值。 在下列範例中， `$i` 變數會在語句的 **重複** 部分中遞增 2 `For` 。

```powershell
for ($i = 0; $i -le 20; $i += 2)
{
    Write-Host $i
}
```

`For`迴圈也可以撰寫在一行，如下列範例所示。

```powershell
for ($i = 0; $i -lt 10; $i++) { Write-Host $i }
```

## <a name="see-also"></a>另請參閱

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Foreach](about_Foreach.md)
