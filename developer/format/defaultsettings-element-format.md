---
title: DefaultSettings 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066340"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="9d546-102">DefaultSettings 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9d546-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="9d546-103">定義套用至的格式化檔案的所有檢視的常見設定。</span><span class="sxs-lookup"><span data-stu-id="9d546-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="9d546-104">一般設定包括顯示錯誤，定義集合展開的資料表中的文字換行。</span><span class="sxs-lookup"><span data-stu-id="9d546-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="9d546-105">組態項目 （格式） DefaultSettings 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="9d546-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9d546-106">語法</span><span class="sxs-lookup"><span data-stu-id="9d546-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9d546-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9d546-107">Attributes and Elements</span></span>

<span data-ttu-id="9d546-108">下列各節說明屬性、 子項目和父項目`DefaultSettings`項目。</span><span class="sxs-lookup"><span data-stu-id="9d546-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9d546-109">屬性</span><span class="sxs-lookup"><span data-stu-id="9d546-109">Attributes</span></span>

<span data-ttu-id="9d546-110">無。</span><span class="sxs-lookup"><span data-stu-id="9d546-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9d546-111">子元素</span><span class="sxs-lookup"><span data-stu-id="9d546-111">Child Elements</span></span>

|<span data-ttu-id="9d546-112">元素</span><span class="sxs-lookup"><span data-stu-id="9d546-112">Element</span></span>|<span data-ttu-id="9d546-113">描述</span><span class="sxs-lookup"><span data-stu-id="9d546-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9d546-114">DisplayError 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="9d546-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="9d546-115">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="9d546-115">Optional element.</span></span><br /><br /> <span data-ttu-id="9d546-116">指定顯示一段資料時，發生錯誤時，會顯示 #ERR 的字串。</span><span class="sxs-lookup"><span data-stu-id="9d546-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="9d546-117">EnumerableExpansions 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="9d546-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="9d546-118">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="9d546-118">Optional element.</span></span><br /><br /> <span data-ttu-id="9d546-119">定義.NET 物件會展開檢視中顯示時的不同方式。</span><span class="sxs-lookup"><span data-stu-id="9d546-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="9d546-120">PropertyCountForTable （格式）</span><span class="sxs-lookup"><span data-stu-id="9d546-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="9d546-121">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="9d546-121">Optional element.</span></span><br /><br /> <span data-ttu-id="9d546-122">指定物件必須具有在資料表檢視中顯示物件的屬性的數目下限。</span><span class="sxs-lookup"><span data-stu-id="9d546-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="9d546-123">ShowError 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="9d546-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="9d546-124">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="9d546-124">Optional element.</span></span><br /><br /> <span data-ttu-id="9d546-125">指定顯示一段資料時，發生錯誤時，會顯示完整的錯誤記錄。</span><span class="sxs-lookup"><span data-stu-id="9d546-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="9d546-126">WrapTables 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="9d546-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="9d546-127">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="9d546-127">Optional element.</span></span><br /><br /> <span data-ttu-id="9d546-128">指定資料表中的資料會移至下一行，是否無法納入資料行的寬度。</span><span class="sxs-lookup"><span data-stu-id="9d546-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9d546-129">父項目</span><span class="sxs-lookup"><span data-stu-id="9d546-129">Parent Elements</span></span>

|<span data-ttu-id="9d546-130">項目</span><span class="sxs-lookup"><span data-stu-id="9d546-130">Element</span></span>|<span data-ttu-id="9d546-131">描述</span><span class="sxs-lookup"><span data-stu-id="9d546-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9d546-132">組態項目</span><span class="sxs-lookup"><span data-stu-id="9d546-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="9d546-133">表示格式化檔案的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="9d546-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9d546-134">備註</span><span class="sxs-lookup"><span data-stu-id="9d546-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="9d546-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d546-135">See Also</span></span>

[<span data-ttu-id="9d546-136">組態項目</span><span class="sxs-lookup"><span data-stu-id="9d546-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="9d546-137">DisplayError 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="9d546-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="9d546-138">EnumerableExpansions 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="9d546-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="9d546-139">PropertyCountForTable （格式）</span><span class="sxs-lookup"><span data-stu-id="9d546-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="9d546-140">ShowError 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="9d546-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="9d546-141">WrapTables 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="9d546-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="9d546-142">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="9d546-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
