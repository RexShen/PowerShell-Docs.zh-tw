---
description: '`enum`語句是用來宣告列舉。 列舉是由一組稱為列舉值清單的命名標籤所組成的相異型別。'
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_enum?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Enum
ms.openlocfilehash: 0b1959ba009119769535c3d39231ff8dab9dc5de
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208048"
---
# <a name="about-enum"></a>關於列舉

## <a name="short-description"></a>簡短描述

`enum`語句是用來宣告列舉。 列舉是由一組稱為列舉值清單的命名標籤所組成的相異型別。

## <a name="long-description"></a>詳細描述

`enum`語句可讓您建立一組強型別的標籤。 該列舉可以在程式碼中使用，而不需要剖析或檢查拼寫錯誤。

列舉會在內部表示為起始值為零的整數。 清單中的第一個標籤會被指派零值。 剩餘的標籤會以連續的數位指派。

在定義中，可以為標籤提供任何整數值。 未指派值的標籤會採用下一個整數值。

## <a name="syntax-basic"></a>基本) 語法 (

```syntax
enum <enum-name> {
    <label> [= <int-value>]
    ...
}
```

## <a name="usage-example"></a>使用範例

下列範例顯示可視為媒體檔案的物件列舉。 定義會將明確的值指派給、、的基礎值 `music` `picture` `video` 。 緊接在明確指派之後的標籤會取得下一個整數值。 您可以將相同的值指派給另一個標籤來建立同義字;請參閱的結構化值： `ogg` 、、 `oga` `mogg` 、或 `jpg` 、 `jpeg` 或 `mpg` `mpeg` 。

```powershell
enum MediaTypes {
    unknown
    music = 10
    mp3
    aac
    ogg = 15
    oga = 15
    mogg = 15
    picture = 20
    jpg
    jpeg = 21
    png
    video = 40
    mpg
    mpeg = 41
    avi
    m4v
}
```

方法會傳回 `GetEnumNames()` 列舉的標籤清單。

```powershell
[MediaTypes].GetEnumNames()
unknown
music
mp3
aac
ogg
oga
mogg
picture
jpg
jpeg
png
video
mpg
mpeg
avi
m4v
```

方法會傳回 `GetEnumValues()` 列舉值的清單。

```powershell
[MediaTypes].GetEnumValues()
unknown
music
mp3
aac
oga
oga
oga
picture
jpeg
jpeg
png
video
mpeg
mpeg
avi
m4v
```

**注意** ： GetEnumNames ( # A1 和 GetEnumValues ( # A3 似乎會傳回相同的結果。
不過，在內部，PowerShell 會將值變更為標籤。 請仔細閱讀此清單，您會注意到， `oga` 和 `mogg` 會在「取得名稱」結果下提及，但不在、和的「取得值」類似輸出下 `jpg` `jpeg` `mpg` `mpeg` 。

```powershell
[MediaTypes].GetEnumName(15)
oga

[MediaTypes].GetEnumNames() | ForEach-Object {
  "{0,-10} {1}" -f $_,[int]([MediaTypes]::$_)
}
unknown    0
music      10
mp3        11
aac        12
ogg        15
oga        15
mogg       15
picture    20
jpg        21
jpeg       21
png        22
video      40
mpg        41
mpeg       41
avi        42
m4v        43
```

## <a name="enumerations-as-flags"></a>作為旗標的列舉

列舉可以定義為位旗標的集合。
在任何指定的點，列舉代表開啟的一或多個旗標。

若要讓列舉能夠正常運作，每個標籤都應該有兩個值的乘冪。

## <a name="syntax-flags"></a>語法 (旗標) 

```syntax
[Flags()] enum <enum-name> {
    <label 0> [= 1]
    <label 1> [= 2]
    <label 2> [= 4]
    <label 3> [= 8]
    ...
}
```

## <a name="flags-usage-example"></a>旗標使用範例

在下列範例中，會建立 *FileAttributes* 列舉。

```powershell
[Flags()] enum FileAttributes {
    Archive = 1
    Compressed = 2
    Device = 4
    Directory = 8
    Encrypted = 16
    Hidden = 32
}

[FileAttributes]$file1 = [FileAttributes]::Archive
[FileAttributes]$file1 +=[FileAttributes]::Compressed
[FileAttributes]$file1 +=  [FileAttributes]::Device
"file1 attributes are: $file1"

[FileAttributes]$file2 = [FileAttributes]28 ## => 16 + 8 + 4
"file2 attributes are: $file2"
```

```output
file1 attributes are: Archive, Compressed, Device
file2 attributes are: Device, Directory, Encrypted
```

若要測試特定的是否已設定，您可以使用二進位比較運算子 `-band` 。 在此範例中，我們會在的值中測試 **裝置** 和 **封存屬性** `$file2` 。

```
PS > ($file2 -band [FileAttributes]::Device) -eq [FileAttributes]::Device
True

PS > ($file2 -band [FileAttributes]::Archive) -eq [FileAttributes]::Archive
False
```
