---
description: 描述聯結運算子 ( 聯結) 如何將多個字串結合成單一字串。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_join?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Join
ms.openlocfilehash: 3e5bf4363adbded29dc58facde00f6597abeb697
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207652"
---
# <a name="about-join"></a><span data-ttu-id="b8c23-104">關於聯結</span><span class="sxs-lookup"><span data-stu-id="b8c23-104">About join</span></span>

## <a name="short-description"></a><span data-ttu-id="b8c23-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="b8c23-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="b8c23-106">描述聯結運算子 ( 聯結) 如何將多個字串結合成單一字串。</span><span class="sxs-lookup"><span data-stu-id="b8c23-106">Describes how the join operator (-join) combines multiple strings into a single string.</span></span>

## <a name="long-description"></a><span data-ttu-id="b8c23-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="b8c23-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="b8c23-108">Join 運算子會將一組字串串連成單一字串。</span><span class="sxs-lookup"><span data-stu-id="b8c23-108">The join operator concatenates a set of strings into a single string.</span></span> <span data-ttu-id="b8c23-109">字串會以它們出現在命令中的順序附加至產生的字串。</span><span class="sxs-lookup"><span data-stu-id="b8c23-109">The strings are appended to the resulting string in the order that they appear in the command.</span></span>

### <a name="syntax"></a><span data-ttu-id="b8c23-110">Syntax</span><span class="sxs-lookup"><span data-stu-id="b8c23-110">Syntax</span></span>

<span data-ttu-id="b8c23-111">下圖顯示聯結運算子的語法。</span><span class="sxs-lookup"><span data-stu-id="b8c23-111">The following diagram shows the syntax for the join operator.</span></span>

```powershell
-Join <String[]>
<String[]> -Join <Delimiter>
```

#### <a name="parameters"></a><span data-ttu-id="b8c23-112">參數</span><span class="sxs-lookup"><span data-stu-id="b8c23-112">Parameters</span></span>

<span data-ttu-id="b8c23-113">String []-指定要聯結的一或多個字串。</span><span class="sxs-lookup"><span data-stu-id="b8c23-113">String[] - Specifies one or more strings to be joined.</span></span>

<span data-ttu-id="b8c23-114">分隔符號-指定在串連字號串之間放置的一或多個字元。</span><span class="sxs-lookup"><span data-stu-id="b8c23-114">Delimiter - Specifies one or more characters placed between the concatenated strings.</span></span> <span data-ttu-id="b8c23-115">預設值為 "" )  ( 不是分隔符號。</span><span class="sxs-lookup"><span data-stu-id="b8c23-115">The default is no delimiter ("").</span></span>

<span data-ttu-id="b8c23-116">備註</span><span class="sxs-lookup"><span data-stu-id="b8c23-116">Remarks</span></span>

<span data-ttu-id="b8c23-117">一元聯結運算子 ( 聯結 <string [] >) 的優先順序高於逗號。</span><span class="sxs-lookup"><span data-stu-id="b8c23-117">The unary join operator (-join <string[]>) has higher precedence than a comma.</span></span> <span data-ttu-id="b8c23-118">如此一來，如果您將以逗號分隔的字串清單提交給一元聯結運算子，則在第一個) 逗號之前 (的第一個字串會提交至聯結運算子。</span><span class="sxs-lookup"><span data-stu-id="b8c23-118">As a result, if you submit a comma-separated list of strings to the unary join operator, only the first string (before the first comma) is submitted to the join operator.</span></span>

<span data-ttu-id="b8c23-119">若要使用一元聯結運算子，請將字串括在括弧中，或將字串儲存在變數中，然後提交變數以進行聯結。</span><span class="sxs-lookup"><span data-stu-id="b8c23-119">To use the unary join operator, enclose the strings in parentheses, or store the strings in a variable, and then submit the variable to join.</span></span>

<span data-ttu-id="b8c23-120">例如：</span><span class="sxs-lookup"><span data-stu-id="b8c23-120">For example:</span></span>

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

### <a name="examples"></a><span data-ttu-id="b8c23-121">範例</span><span class="sxs-lookup"><span data-stu-id="b8c23-121">Examples</span></span>

<span data-ttu-id="b8c23-122">下列語句會加入三個字串：</span><span class="sxs-lookup"><span data-stu-id="b8c23-122">The following statement joins three strings:</span></span>

```powershell
-join ("Windows", "PowerShell", "2.0")
WindowsPowerShell2.0
```

<span data-ttu-id="b8c23-123">下列語句會加入以空格分隔的三個字串：</span><span class="sxs-lookup"><span data-stu-id="b8c23-123">The following statement joins three strings delimited by a space:</span></span>

```powershell
"Windows", "PowerShell", "2.0" -join " "
Windows PowerShell 2.0
```

<span data-ttu-id="b8c23-124">下列語句會使用多重字元分隔符號來聯結三個字串：</span><span class="sxs-lookup"><span data-stu-id="b8c23-124">The following statements use a multiple-character delimiter to join three strings:</span></span>

```powershell
$a = "WIND", "S P", "ERSHELL"
$a -join "OW"
WINDOWS POWERSHELL
```

<span data-ttu-id="b8c23-125">下列語句會將此字串中的行聯結成單一字串。</span><span class="sxs-lookup"><span data-stu-id="b8c23-125">The following statement joins the lines in a here-string into a single string.</span></span> <span data-ttu-id="b8c23-126">因為這裡的字串是一個字串，所以必須先分割在此字串中的行，然後才能聯結。</span><span class="sxs-lookup"><span data-stu-id="b8c23-126">Because a here-string is one string, the lines in the here-string must be split before they can be joined.</span></span> <span data-ttu-id="b8c23-127">您可以使用這個方法，將 XML 檔案中已儲存的字串重新加入至這個字串：</span><span class="sxs-lookup"><span data-stu-id="b8c23-127">You can use this method to rejoin the strings in an XML file that has been saved in a here-string:</span></span>

```powershell
$a = @'
a
b
c
'@

(-split $a) -join " "
a b c
```

## <a name="see-also"></a><span data-ttu-id="b8c23-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8c23-128">SEE ALSO</span></span>

[<span data-ttu-id="b8c23-129">about_Operators</span><span class="sxs-lookup"><span data-stu-id="b8c23-129">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="b8c23-130">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="b8c23-130">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="b8c23-131">about_Split</span><span class="sxs-lookup"><span data-stu-id="b8c23-131">about_Split</span></span>](about_Split.md)
