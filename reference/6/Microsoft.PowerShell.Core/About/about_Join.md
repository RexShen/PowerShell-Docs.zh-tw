---
description: 描述聯結運算子 ( 聯結) 如何將多個字串結合成單一字串。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_join?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Join
ms.openlocfilehash: adc65e688894ce71ea386fd2b21799612df789a0
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207060"
---
# <a name="about-join"></a>關於聯結

## <a name="short-description"></a>簡短描述
描述聯結運算子 ( 聯結) 如何將多個字串結合成單一字串。

## <a name="long-description"></a>詳細描述

Join 運算子會將一組字串串連成單一字串。 字串會以它們出現在命令中的順序附加至產生的字串。

### <a name="syntax"></a>Syntax

下圖顯示聯結運算子的語法。

```powershell
-Join <String[]>
<String[]> -Join <Delimiter>
```

#### <a name="parameters"></a>參數

String []-指定要聯結的一或多個字串。

分隔符號-指定在串連字號串之間放置的一或多個字元。 預設值為 "" )  ( 不是分隔符號。

備註

一元聯結運算子 ( 聯結 <string [] >) 的優先順序高於逗號。 如此一來，如果您將以逗號分隔的字串清單提交給一元聯結運算子，則在第一個) 逗號之前 (的第一個字串會提交至聯結運算子。

若要使用一元聯結運算子，請將字串括在括弧中，或將字串儲存在變數中，然後提交變數以進行聯結。

例如：

```powershell
-join "a", "b", "c"
a
b
c

-join ("a", "b", "c")
abc

$z = "a", "b", "c"
-join $z
abc
```

### <a name="examples"></a>範例

下列語句會加入三個字串：

```powershell
-join ("Windows", "PowerShell", "2.0")
WindowsPowerShell2.0
```

下列語句會加入以空格分隔的三個字串：

```powershell
"Windows", "PowerShell", "2.0" -join " "
Windows PowerShell 2.0
```

下列語句會使用多重字元分隔符號來聯結三個字串：

```powershell
$a = "WIND", "S P", "ERSHELL"
$a -join "OW"
WINDOWS POWERSHELL
```

下列語句會將此字串中的行聯結成單一字串。 因為這裡的字串是一個字串，所以必須先分割在此字串中的行，然後才能聯結。 您可以使用這個方法，將 XML 檔案中已儲存的字串重新加入至這個字串：

```powershell
$a = @'
a
b
c
'@

(-split $a) -join " "
a b c
```

## <a name="see-also"></a>另請參閱

[about_Operators](about_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Split](about_Split.md)
