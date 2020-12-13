---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSet 元素 (格式)
description: SelectionSet 元素 (格式)
ms.openlocfilehash: 944aa83569ad8ca789746a71f60e5da5c19fbf01
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647866"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="6a704-103">SelectionSet 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="6a704-103">SelectionSet Element (Format)</span></span>

<span data-ttu-id="6a704-104">定義一組可由集合名稱參考的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="6a704-104">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="6a704-105">Configuration 元素 (格式) SelectionSets 元素 (格式) SelectionSet 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="6a704-105">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6a704-106">語法</span><span class="sxs-lookup"><span data-stu-id="6a704-106">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6a704-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6a704-107">Attributes and Elements</span></span>

<span data-ttu-id="6a704-108">下列章節說明屬性、子專案和元素的父元素 `SelectionSet` 。</span><span class="sxs-lookup"><span data-stu-id="6a704-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="6a704-109">每個選擇集都必須有名稱，而且必須指定集合的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="6a704-109">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="6a704-110">屬性</span><span class="sxs-lookup"><span data-stu-id="6a704-110">Attributes</span></span>

<span data-ttu-id="6a704-111">無。</span><span class="sxs-lookup"><span data-stu-id="6a704-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6a704-112">子元素</span><span class="sxs-lookup"><span data-stu-id="6a704-112">Child Elements</span></span>

|<span data-ttu-id="6a704-113">元素</span><span class="sxs-lookup"><span data-stu-id="6a704-113">Element</span></span>|<span data-ttu-id="6a704-114">描述</span><span class="sxs-lookup"><span data-stu-id="6a704-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a704-115">SelectionSet 的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="6a704-115">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="6a704-116">必要元素。</span><span class="sxs-lookup"><span data-stu-id="6a704-116">Required element.</span></span><br /><br /> <span data-ttu-id="6a704-117">指定用來參考選取集的名稱。</span><span class="sxs-lookup"><span data-stu-id="6a704-117">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="6a704-118">類型元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="6a704-118">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="6a704-119">必要元素。</span><span class="sxs-lookup"><span data-stu-id="6a704-119">Required element.</span></span><br /><br /> <span data-ttu-id="6a704-120">定義選取專案集中的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="6a704-120">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6a704-121">父項目</span><span class="sxs-lookup"><span data-stu-id="6a704-121">Parent Elements</span></span>

|<span data-ttu-id="6a704-122">元素</span><span class="sxs-lookup"><span data-stu-id="6a704-122">Element</span></span>|<span data-ttu-id="6a704-123">描述</span><span class="sxs-lookup"><span data-stu-id="6a704-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a704-124">SelectionSets 元素格式</span><span class="sxs-lookup"><span data-stu-id="6a704-124">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="6a704-125">定義可供格式化檔案的所有視圖使用的通用 .NET 物件集。</span><span class="sxs-lookup"><span data-stu-id="6a704-125">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6a704-126">備註</span><span class="sxs-lookup"><span data-stu-id="6a704-126">Remarks</span></span>

<span data-ttu-id="6a704-127">當您有一組要使用單一名稱來參考的相關物件時，例如一組透過繼承相關的物件，您可以使用選取集。</span><span class="sxs-lookup"><span data-stu-id="6a704-127">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="6a704-128">定義您的視圖時，您可以使用選取集的名稱來指定物件集合，而不是列出每個視圖內的所有物件。</span><span class="sxs-lookup"><span data-stu-id="6a704-128">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="6a704-129">在定義格式化檔案的視圖或視圖的定義時，會以名稱指定常用的選取集。</span><span class="sxs-lookup"><span data-stu-id="6a704-129">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="6a704-130">在這些情況下， `SelectionSetName` 和元素的子 `ViewSelectedBy` 元素 `EntrySelectedBy` 會指定要使用的集合。</span><span class="sxs-lookup"><span data-stu-id="6a704-130">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="6a704-131">如需選取集的詳細資訊，請參閱 [定義物件集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="6a704-131">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="6a704-132">範例</span><span class="sxs-lookup"><span data-stu-id="6a704-132">Example</span></span>

<span data-ttu-id="6a704-133">下列範例顯示 `SelectionSet` 定義四個 .net 類型的元素。</span><span class="sxs-lookup"><span data-stu-id="6a704-133">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

```xml
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

## <a name="see-also"></a><span data-ttu-id="6a704-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a704-134">See Also</span></span>

[<span data-ttu-id="6a704-135">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="6a704-135">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="6a704-136">SelectionSet (格式的 Name 元素) </span><span class="sxs-lookup"><span data-stu-id="6a704-136">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="6a704-137">SelectionSets 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="6a704-137">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="6a704-138">類型元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="6a704-138">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="6a704-139">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="6a704-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
