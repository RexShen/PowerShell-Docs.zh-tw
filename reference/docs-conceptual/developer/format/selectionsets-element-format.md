---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSets 元素 (格式)
description: SelectionSets 元素 (格式)
ms.openlocfilehash: e5c928dfb82bc6963b4a87aef9ec06d34cacfdcb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654931"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="38b83-103">SelectionSets 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="38b83-103">SelectionSets Element (Format)</span></span>

<span data-ttu-id="38b83-104">定義可供格式化檔案的所有視圖使用的通用 .NET 物件集。</span><span class="sxs-lookup"><span data-stu-id="38b83-104">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="38b83-105">格式設定檔案的視圖和控制項可以使用選取範圍的名稱，參考一組完整的物件。</span><span class="sxs-lookup"><span data-stu-id="38b83-105">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="38b83-106">Configuration 元素 SelectionSets 元素格式</span><span class="sxs-lookup"><span data-stu-id="38b83-106">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="38b83-107">語法</span><span class="sxs-lookup"><span data-stu-id="38b83-107">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="38b83-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="38b83-108">Attributes and Elements</span></span>

<span data-ttu-id="38b83-109">下列各節描述專案的屬性、子項目和父元素 `SelectionSets` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-109">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="38b83-110">每個子專案都會定義一組可由集合名稱參考的物件。</span><span class="sxs-lookup"><span data-stu-id="38b83-110">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="38b83-111">子項目的順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="38b83-111">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="38b83-112">屬性</span><span class="sxs-lookup"><span data-stu-id="38b83-112">Attributes</span></span>

<span data-ttu-id="38b83-113">無。</span><span class="sxs-lookup"><span data-stu-id="38b83-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="38b83-114">子元素</span><span class="sxs-lookup"><span data-stu-id="38b83-114">Child Elements</span></span>

|<span data-ttu-id="38b83-115">元素</span><span class="sxs-lookup"><span data-stu-id="38b83-115">Element</span></span>|<span data-ttu-id="38b83-116">描述</span><span class="sxs-lookup"><span data-stu-id="38b83-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38b83-117">SelectionSet 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="38b83-117">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="38b83-118">必要元素。</span><span class="sxs-lookup"><span data-stu-id="38b83-118">Required element.</span></span><br /><br /> <span data-ttu-id="38b83-119">定義可由集合名稱參考的一組 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="38b83-119">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="38b83-120">父項目</span><span class="sxs-lookup"><span data-stu-id="38b83-120">Parent Elements</span></span>

|<span data-ttu-id="38b83-121">元素</span><span class="sxs-lookup"><span data-stu-id="38b83-121">Element</span></span>|<span data-ttu-id="38b83-122">描述</span><span class="sxs-lookup"><span data-stu-id="38b83-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38b83-123">組態元素</span><span class="sxs-lookup"><span data-stu-id="38b83-123">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="38b83-124">代表格式化檔案的最上層元素。</span><span class="sxs-lookup"><span data-stu-id="38b83-124">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="38b83-125">備註</span><span class="sxs-lookup"><span data-stu-id="38b83-125">Remarks</span></span>

<span data-ttu-id="38b83-126">當您有一組要使用單一名稱來參考的相關物件時，例如一組透過繼承相關的物件，您可以使用選取集。</span><span class="sxs-lookup"><span data-stu-id="38b83-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="38b83-127">定義您的視圖時，您可以使用選取集的名稱來指定物件集合，而不是列出每個視圖內的所有物件。</span><span class="sxs-lookup"><span data-stu-id="38b83-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="38b83-128">在定義格式化檔案的視圖或視圖的定義時，會以名稱指定常用的選取集。</span><span class="sxs-lookup"><span data-stu-id="38b83-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="38b83-129">在這些情況下， `SelectionSetName` 和元素的子 `ViewSelectedBy` 元素 `EntrySelectedBy` 會指定要使用的集合。</span><span class="sxs-lookup"><span data-stu-id="38b83-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="38b83-130">如需選取集的詳細資訊，請參閱 [定義物件集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="38b83-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="38b83-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38b83-131">See Also</span></span>

[<span data-ttu-id="38b83-132">組態元素</span><span class="sxs-lookup"><span data-stu-id="38b83-132">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="38b83-133">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="38b83-133">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="38b83-134">SelectionSet 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="38b83-134">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="38b83-135">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="38b83-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
