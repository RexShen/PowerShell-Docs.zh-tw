---
title: DefaultSettings 元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7da7948fc0814e38a8f3910596e223470ec27d75
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787728"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="8e0bc-102">DefaultSettings 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8e0bc-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="8e0bc-103">定義套用至格式化檔案所有視圖的一般設定。</span><span class="sxs-lookup"><span data-stu-id="8e0bc-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="8e0bc-104">一般設定包括顯示錯誤、在資料表中將文字換行、定義如何擴充集合等等。</span><span class="sxs-lookup"><span data-stu-id="8e0bc-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="8e0bc-105">Configuration 元素 (格式) DefaultSettings 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="8e0bc-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8e0bc-106">語法</span><span class="sxs-lookup"><span data-stu-id="8e0bc-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8e0bc-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8e0bc-107">Attributes and Elements</span></span>

<span data-ttu-id="8e0bc-108">下列各節說明屬性、子專案和元素的父元素 `DefaultSettings` 。</span><span class="sxs-lookup"><span data-stu-id="8e0bc-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8e0bc-109">屬性</span><span class="sxs-lookup"><span data-stu-id="8e0bc-109">Attributes</span></span>

<span data-ttu-id="8e0bc-110">無。</span><span class="sxs-lookup"><span data-stu-id="8e0bc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8e0bc-111">子元素</span><span class="sxs-lookup"><span data-stu-id="8e0bc-111">Child Elements</span></span>

|<span data-ttu-id="8e0bc-112">元素</span><span class="sxs-lookup"><span data-stu-id="8e0bc-112">Element</span></span>|<span data-ttu-id="8e0bc-113">描述</span><span class="sxs-lookup"><span data-stu-id="8e0bc-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8e0bc-114">DisplayError 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8e0bc-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="8e0bc-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="8e0bc-115">Optional element.</span></span><br /><br /> <span data-ttu-id="8e0bc-116">指定在顯示資料時，如果發生錯誤，就會顯示字串 #ERR。</span><span class="sxs-lookup"><span data-stu-id="8e0bc-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="8e0bc-117">EnumerableExpansions 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8e0bc-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="8e0bc-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="8e0bc-118">Optional element.</span></span><br /><br /> <span data-ttu-id="8e0bc-119">定義在視圖中顯示 .NET 物件時，要展開的不同方式。</span><span class="sxs-lookup"><span data-stu-id="8e0bc-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="8e0bc-120">PropertyCountForTable (格式) </span><span class="sxs-lookup"><span data-stu-id="8e0bc-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="8e0bc-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="8e0bc-121">Optional element.</span></span><br /><br /> <span data-ttu-id="8e0bc-122">指定物件在資料表視圖中顯示物件時必須擁有的最小屬性數目。</span><span class="sxs-lookup"><span data-stu-id="8e0bc-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="8e0bc-123">ShowError 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8e0bc-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="8e0bc-124">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="8e0bc-124">Optional element.</span></span><br /><br /> <span data-ttu-id="8e0bc-125">指定顯示資料時，如果發生錯誤，就會顯示完整的錯誤記錄。</span><span class="sxs-lookup"><span data-stu-id="8e0bc-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="8e0bc-126">WrapTables 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8e0bc-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="8e0bc-127">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="8e0bc-127">Optional element.</span></span><br /><br /> <span data-ttu-id="8e0bc-128">指定如果資料表中的資料不符合資料行的寬度，則會將它移到下一行。</span><span class="sxs-lookup"><span data-stu-id="8e0bc-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8e0bc-129">父項目</span><span class="sxs-lookup"><span data-stu-id="8e0bc-129">Parent Elements</span></span>

|<span data-ttu-id="8e0bc-130">元素</span><span class="sxs-lookup"><span data-stu-id="8e0bc-130">Element</span></span>|<span data-ttu-id="8e0bc-131">描述</span><span class="sxs-lookup"><span data-stu-id="8e0bc-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8e0bc-132">組態元素</span><span class="sxs-lookup"><span data-stu-id="8e0bc-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="8e0bc-133">代表格式化檔案的最上層元素。</span><span class="sxs-lookup"><span data-stu-id="8e0bc-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8e0bc-134">備註</span><span class="sxs-lookup"><span data-stu-id="8e0bc-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="8e0bc-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e0bc-135">See Also</span></span>

[<span data-ttu-id="8e0bc-136">組態元素</span><span class="sxs-lookup"><span data-stu-id="8e0bc-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="8e0bc-137">DisplayError 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8e0bc-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="8e0bc-138">EnumerableExpansions 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8e0bc-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="8e0bc-139">PropertyCountForTable (格式) </span><span class="sxs-lookup"><span data-stu-id="8e0bc-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="8e0bc-140">ShowError 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8e0bc-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="8e0bc-141">WrapTables 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8e0bc-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="8e0bc-142">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="8e0bc-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
