---
ms.date: 09/13/2016
ms.topic: reference
title: 類型的 TypeName 元素 (格式)
description: 類型的 TypeName 元素 (格式)
ms.openlocfilehash: c656b8e7e5877b72ff2164e5b417857273cada61
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664612"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="46d5b-103">類型的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="46d5b-103">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="46d5b-104">指定屬於選取集之物件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="46d5b-104">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="46d5b-105">Configuration 元素 (格式) SelectionSets 元素 (格式) SelectionSet 專案 (格式) 類型專案 (格式) 格式 (類型) 格式</span><span class="sxs-lookup"><span data-stu-id="46d5b-105">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="46d5b-106">語法</span><span class="sxs-lookup"><span data-stu-id="46d5b-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="46d5b-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="46d5b-107">Attributes and Elements</span></span>

<span data-ttu-id="46d5b-108">下列章節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="46d5b-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="46d5b-109">`TypeName`選取專案集中必須包含至少一個元素。</span><span class="sxs-lookup"><span data-stu-id="46d5b-109">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="46d5b-110">屬性</span><span class="sxs-lookup"><span data-stu-id="46d5b-110">Attributes</span></span>

<span data-ttu-id="46d5b-111">無。</span><span class="sxs-lookup"><span data-stu-id="46d5b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="46d5b-112">子元素</span><span class="sxs-lookup"><span data-stu-id="46d5b-112">Child Elements</span></span>

<span data-ttu-id="46d5b-113">無。</span><span class="sxs-lookup"><span data-stu-id="46d5b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="46d5b-114">父項目</span><span class="sxs-lookup"><span data-stu-id="46d5b-114">Parent Elements</span></span>

|<span data-ttu-id="46d5b-115">元素</span><span class="sxs-lookup"><span data-stu-id="46d5b-115">Element</span></span>|<span data-ttu-id="46d5b-116">描述</span><span class="sxs-lookup"><span data-stu-id="46d5b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="46d5b-117">類型元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="46d5b-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="46d5b-118">定義選取專案集中的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="46d5b-118">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="46d5b-119">文字值</span><span class="sxs-lookup"><span data-stu-id="46d5b-119">Text Value</span></span>

<span data-ttu-id="46d5b-120">指定 .NET 類型的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="46d5b-120">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="46d5b-121">備註</span><span class="sxs-lookup"><span data-stu-id="46d5b-121">Remarks</span></span>

<span data-ttu-id="46d5b-122">當您有一組要使用單一名稱來參考的相關物件時，例如一組透過繼承相關的物件，您可以使用選取集。</span><span class="sxs-lookup"><span data-stu-id="46d5b-122">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="46d5b-123">定義您的視圖時，您可以使用選取集的名稱來指定物件集合，而不是列出每個視圖內的所有物件。</span><span class="sxs-lookup"><span data-stu-id="46d5b-123">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="46d5b-124">定義格式化檔案的視圖時，會依名稱來指定常用的選取集。</span><span class="sxs-lookup"><span data-stu-id="46d5b-124">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="46d5b-125">在這些情況下， `SelectionSetName` view 專案的子項目會 `ViewSelectedBy` 指定集合。</span><span class="sxs-lookup"><span data-stu-id="46d5b-125">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="46d5b-126">不過，view 的不同專案也可以指定僅套用至該專案的選項組。</span><span class="sxs-lookup"><span data-stu-id="46d5b-126">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="46d5b-127">如需選取集的詳細資訊，請參閱 [定義物件集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="46d5b-127">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="46d5b-128">範例</span><span class="sxs-lookup"><span data-stu-id="46d5b-128">Example</span></span>

<span data-ttu-id="46d5b-129">下列範例顯示 `SelectionSet` 定義四個 .net 類型的元素。</span><span class="sxs-lookup"><span data-stu-id="46d5b-129">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

```
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a><span data-ttu-id="46d5b-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46d5b-130">See Also</span></span>

[<span data-ttu-id="46d5b-131">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="46d5b-131">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="46d5b-132">SelectionSet 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="46d5b-132">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="46d5b-133">SelectionSets 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="46d5b-133">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="46d5b-134">類型元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="46d5b-134">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="46d5b-135">撰寫 Windows PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="46d5b-135">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
