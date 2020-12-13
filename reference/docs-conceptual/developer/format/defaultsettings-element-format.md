---
ms.date: 09/13/2016
ms.topic: reference
title: DefaultSettings 元素 (格式)
description: DefaultSettings 元素 (格式)
ms.openlocfilehash: 1c2055b38a416fe2d75fa20c6c87e92d9eed4285
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666717"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="52129-103">DefaultSettings 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="52129-103">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="52129-104">定義適用于格式檔案所有視圖的一般設定。</span><span class="sxs-lookup"><span data-stu-id="52129-104">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="52129-105">一般設定包括顯示錯誤、在資料表中包裝文字、定義集合的擴充方式等等。</span><span class="sxs-lookup"><span data-stu-id="52129-105">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="52129-106">Configuration 元素 (格式) DefaultSettings 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="52129-106">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="52129-107">語法</span><span class="sxs-lookup"><span data-stu-id="52129-107">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="52129-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="52129-108">Attributes and Elements</span></span>

<span data-ttu-id="52129-109">下列各節說明屬性、子專案和元素的父元素 `DefaultSettings` 。</span><span class="sxs-lookup"><span data-stu-id="52129-109">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="52129-110">屬性</span><span class="sxs-lookup"><span data-stu-id="52129-110">Attributes</span></span>

<span data-ttu-id="52129-111">無。</span><span class="sxs-lookup"><span data-stu-id="52129-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="52129-112">子元素</span><span class="sxs-lookup"><span data-stu-id="52129-112">Child Elements</span></span>

|<span data-ttu-id="52129-113">元素</span><span class="sxs-lookup"><span data-stu-id="52129-113">Element</span></span>|<span data-ttu-id="52129-114">描述</span><span class="sxs-lookup"><span data-stu-id="52129-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="52129-115">DisplayError 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="52129-115">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="52129-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="52129-116">Optional element.</span></span><br /><br /> <span data-ttu-id="52129-117">指定當顯示資料時，出現錯誤時，會顯示字串 #ERR。</span><span class="sxs-lookup"><span data-stu-id="52129-117">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="52129-118">EnumerableExpansions 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="52129-118">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="52129-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="52129-119">Optional element.</span></span><br /><br /> <span data-ttu-id="52129-120">定義在顯示于視圖時，.NET 物件展開的不同方式。</span><span class="sxs-lookup"><span data-stu-id="52129-120">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="52129-121">PropertyCountForTable (格式) </span><span class="sxs-lookup"><span data-stu-id="52129-121">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="52129-122">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="52129-122">Optional element.</span></span><br /><br /> <span data-ttu-id="52129-123">指定物件在資料表視圖中顯示物件時必須擁有的最小屬性數目。</span><span class="sxs-lookup"><span data-stu-id="52129-123">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="52129-124">ShowError 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="52129-124">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="52129-125">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="52129-125">Optional element.</span></span><br /><br /> <span data-ttu-id="52129-126">指定當顯示資料時，發生錯誤時，就會顯示完整的錯誤記錄。</span><span class="sxs-lookup"><span data-stu-id="52129-126">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="52129-127">WrapTables 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="52129-127">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="52129-128">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="52129-128">Optional element.</span></span><br /><br /> <span data-ttu-id="52129-129">指定當資料表中的資料不符合資料行的寬度時，會將資料表中的資料移到下一行。</span><span class="sxs-lookup"><span data-stu-id="52129-129">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="52129-130">父項目</span><span class="sxs-lookup"><span data-stu-id="52129-130">Parent Elements</span></span>

|<span data-ttu-id="52129-131">元素</span><span class="sxs-lookup"><span data-stu-id="52129-131">Element</span></span>|<span data-ttu-id="52129-132">描述</span><span class="sxs-lookup"><span data-stu-id="52129-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="52129-133">組態元素</span><span class="sxs-lookup"><span data-stu-id="52129-133">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="52129-134">代表格式化檔案的最上層元素。</span><span class="sxs-lookup"><span data-stu-id="52129-134">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="52129-135">備註</span><span class="sxs-lookup"><span data-stu-id="52129-135">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="52129-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52129-136">See Also</span></span>

[<span data-ttu-id="52129-137">組態元素</span><span class="sxs-lookup"><span data-stu-id="52129-137">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="52129-138">DisplayError 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="52129-138">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="52129-139">EnumerableExpansions 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="52129-139">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="52129-140">PropertyCountForTable (格式) </span><span class="sxs-lookup"><span data-stu-id="52129-140">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="52129-141">ShowError 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="52129-141">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="52129-142">WrapTables 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="52129-142">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="52129-143">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="52129-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
