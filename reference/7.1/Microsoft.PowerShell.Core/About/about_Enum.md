---
description: '`enum`語句是用來宣告列舉。 列舉是由一組稱為列舉值清單的命名標籤所組成的相異型別。'
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_enum?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Enum
ms.openlocfilehash: 1ffb18ab98fbd40b407abfe32c71027315b69621
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207339"
---
# <a name="about-enum"></a><span data-ttu-id="9f4f9-105">關於列舉</span><span class="sxs-lookup"><span data-stu-id="9f4f9-105">About Enum</span></span>

## <a name="short-description"></a><span data-ttu-id="9f4f9-106">簡短描述</span><span class="sxs-lookup"><span data-stu-id="9f4f9-106">SHORT DESCRIPTION</span></span>
<span data-ttu-id="9f4f9-107">`enum`語句是用來宣告列舉。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-107">The `enum` statement is used to declare an enumeration.</span></span> <span data-ttu-id="9f4f9-108">列舉是由一組稱為列舉值清單的命名標籤所組成的相異型別。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-108">An enumeration is a distinct type that consists of a set of named labels called the enumerator list.</span></span>

## <a name="long-description"></a><span data-ttu-id="9f4f9-109">詳細描述</span><span class="sxs-lookup"><span data-stu-id="9f4f9-109">LONG DESCRIPTION</span></span>

<span data-ttu-id="9f4f9-110">`enum`語句可讓您建立一組強型別的標籤。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-110">The `enum` statement allows you to create a strongly typed set of labels.</span></span> <span data-ttu-id="9f4f9-111">該列舉可以在程式碼中使用，而不需要剖析或檢查拼寫錯誤。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-111">That enumeration can be used in the code without having to parse or check for spelling errors.</span></span>

<span data-ttu-id="9f4f9-112">列舉會在內部表示為起始值為零的整數。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-112">Enumerations are internally represented as integers with a starting value of zero.</span></span> <span data-ttu-id="9f4f9-113">清單中的第一個標籤會被指派零值。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-113">The first label in the list is assigned the value zero.</span></span> <span data-ttu-id="9f4f9-114">剩餘的標籤會以連續的數位指派。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-114">The remaining labels are assigned with consecutive numbers.</span></span>

<span data-ttu-id="9f4f9-115">在定義中，可以為標籤提供任何整數值。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-115">In the definition, labels can be given any integer value.</span></span> <span data-ttu-id="9f4f9-116">未指派值的標籤會採用下一個整數值。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-116">Labels with no value assigned take the next integer value.</span></span>

## <a name="syntax-basic"></a><span data-ttu-id="9f4f9-117">基本) 語法 (</span><span class="sxs-lookup"><span data-stu-id="9f4f9-117">Syntax (basic)</span></span>

```syntax
enum <enum-name> {
    <label> [= <int-value>]
    ...
}
```

## <a name="usage-example"></a><span data-ttu-id="9f4f9-118">使用範例</span><span class="sxs-lookup"><span data-stu-id="9f4f9-118">Usage example</span></span>

<span data-ttu-id="9f4f9-119">下列範例顯示可視為媒體檔案的物件列舉。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-119">The following example shows an enumeration of objects that can be seen as media files.</span></span> <span data-ttu-id="9f4f9-120">定義會將明確的值指派給、、的基礎值 `music` `picture` `video` 。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-120">The definition assigns explicit values to the underlying values of `music`, `picture`, `video`.</span></span> <span data-ttu-id="9f4f9-121">緊接在明確指派之後的標籤會取得下一個整數值。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-121">Labels immediately following an explicit assignment get the next integer value.</span></span> <span data-ttu-id="9f4f9-122">您可以將相同的值指派給另一個標籤來建立同義字;請參閱的結構化值： `ogg` 、、 `oga` `mogg` 、或 `jpg` 、 `jpeg` 或 `mpg` `mpeg` 。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-122">Synonyms can be created by assigning the same value to another label; see the constructed values for: `ogg`, `oga`, `mogg`, or `jpg`, `jpeg`, or `mpg`, `mpeg`.</span></span>

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

<span data-ttu-id="9f4f9-123">方法會傳回 `GetEnumNames()` 列舉的標籤清單。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-123">The `GetEnumNames()` method returns the list of the labels for the enumeration.</span></span>

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

<span data-ttu-id="9f4f9-124">方法會傳回 `GetEnumValues()` 列舉值的清單。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-124">The `GetEnumValues()` method returns the list of the values for the enumeration.</span></span>

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

<span data-ttu-id="9f4f9-125">**注意** ： GetEnumNames ( # A1 和 GetEnumValues ( # A3 似乎會傳回相同的結果。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-125">**Note** : GetEnumNames() and GetEnumValues() seem to return the same results.</span></span>
<span data-ttu-id="9f4f9-126">不過，在內部，PowerShell 會將值變更為標籤。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-126">However, internally, PowerShell is changing values into labels.</span></span> <span data-ttu-id="9f4f9-127">請仔細閱讀此清單，您會注意到， `oga` 和 `mogg` 會在「取得名稱」結果下提及，但不在、和的「取得值」類似輸出下 `jpg` `jpeg` `mpg` `mpeg` 。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-127">Read the list carefully and you'll notice that `oga` and `mogg` are mentioned under the 'Get Names' results, but not under the 'Get Values' similar output for `jpg`, `jpeg`, and `mpg`, `mpeg`.</span></span>

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

## <a name="enumerations-as-flags"></a><span data-ttu-id="9f4f9-128">作為旗標的列舉</span><span class="sxs-lookup"><span data-stu-id="9f4f9-128">Enumerations as flags</span></span>

<span data-ttu-id="9f4f9-129">列舉可以定義為位旗標的集合。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-129">Enumerations can be defined as a collection of bit flags.</span></span>
<span data-ttu-id="9f4f9-130">在任何指定的點，列舉代表開啟的一或多個旗標。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-130">Where, at any given point the enumeration represents one or more of those flags turned on.</span></span>

<span data-ttu-id="9f4f9-131">若要讓列舉能夠正常運作，每個標籤都應該有兩個值的乘冪。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-131">For enumerations as flags to work properly, each label should have a power of two value.</span></span>

## <a name="syntax-flags"></a><span data-ttu-id="9f4f9-132">語法 (旗標) </span><span class="sxs-lookup"><span data-stu-id="9f4f9-132">Syntax (flags)</span></span>

```syntax
[Flags()] enum <enum-name> {
    <label 0> [= 1]
    <label 1> [= 2]
    <label 2> [= 4]
    <label 3> [= 8]
    ...
}
```

## <a name="flags-usage-example"></a><span data-ttu-id="9f4f9-133">旗標使用範例</span><span class="sxs-lookup"><span data-stu-id="9f4f9-133">Flags usage example</span></span>

<span data-ttu-id="9f4f9-134">在下列範例中，會建立 *FileAttributes* 列舉。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-134">In the following example the *FileAttributes* enumeration is created.</span></span>

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

<span data-ttu-id="9f4f9-135">若要測試特定的是否已設定，您可以使用二進位比較運算子 `-band` 。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-135">To test that a specific is set, you can use the binary comparison operator `-band`.</span></span> <span data-ttu-id="9f4f9-136">在此範例中，我們會在的值中測試 **裝置** 和 **封存屬性** `$file2` 。</span><span class="sxs-lookup"><span data-stu-id="9f4f9-136">In this example, we test for the **Device** and the **Archive** attributes in the value of `$file2`.</span></span>

```
PS > ($file2 -band [FileAttributes]::Device) -eq [FileAttributes]::Device
True

PS > ($file2 -band [FileAttributes]::Archive) -eq [FileAttributes]::Archive
False
```

