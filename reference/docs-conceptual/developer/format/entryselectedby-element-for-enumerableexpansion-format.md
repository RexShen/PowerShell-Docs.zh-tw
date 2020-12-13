---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansion 的 EntrySelectedBy 元素 (格式)
description: EnumerableExpansion 的 EntrySelectedBy 元素 (格式)
ms.openlocfilehash: 8b2fff2d0b14d0622d0be2c5af3a95194c733a73
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652321"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="5b8b3-103">EnumerableExpansion 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5b8b3-103">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="5b8b3-104">定義使用此定義的 .NET 類型或必須存在的條件，才能使用這個定義。</span><span class="sxs-lookup"><span data-stu-id="5b8b3-104">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="5b8b3-105">Configuration 元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 元素 (格式) EnumerableExpansion 元素 (格式) 之 entryselectedby 專案的 EnumerableExpansion (格式) </span><span class="sxs-lookup"><span data-stu-id="5b8b3-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5b8b3-106">語法</span><span class="sxs-lookup"><span data-stu-id="5b8b3-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5b8b3-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5b8b3-107">Attributes and Elements</span></span>

<span data-ttu-id="5b8b3-108">下列各節說明屬性、子專案和元素的父元素 `EntrySelectedBy` 。</span><span class="sxs-lookup"><span data-stu-id="5b8b3-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5b8b3-109">屬性</span><span class="sxs-lookup"><span data-stu-id="5b8b3-109">Attributes</span></span>

<span data-ttu-id="5b8b3-110">無。</span><span class="sxs-lookup"><span data-stu-id="5b8b3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5b8b3-111">子元素</span><span class="sxs-lookup"><span data-stu-id="5b8b3-111">Child Elements</span></span>

|<span data-ttu-id="5b8b3-112">元素</span><span class="sxs-lookup"><span data-stu-id="5b8b3-112">Element</span></span>|<span data-ttu-id="5b8b3-113">描述</span><span class="sxs-lookup"><span data-stu-id="5b8b3-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5b8b3-114">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5b8b3-114">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="5b8b3-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="5b8b3-115">Optional element.</span></span><br /><br /> <span data-ttu-id="5b8b3-116">定義必須存在才能展開這個定義之集合物件的條件。</span><span class="sxs-lookup"><span data-stu-id="5b8b3-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="5b8b3-117">EnumerableExpansion 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5b8b3-117">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="5b8b3-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="5b8b3-118">Optional element.</span></span><br /><br /> <span data-ttu-id="5b8b3-119">指定一組 .NET 型別，這些型別會使用此定義來擴充集合物件的方式。</span><span class="sxs-lookup"><span data-stu-id="5b8b3-119">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="5b8b3-120">EnumerableExpansion 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5b8b3-120">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="5b8b3-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="5b8b3-121">Optional element.</span></span><br /><br /> <span data-ttu-id="5b8b3-122">指定 .NET 型別，此型別會使用此定義來擴充集合物件的方式。</span><span class="sxs-lookup"><span data-stu-id="5b8b3-122">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5b8b3-123">父項目</span><span class="sxs-lookup"><span data-stu-id="5b8b3-123">Parent Elements</span></span>

|<span data-ttu-id="5b8b3-124">元素</span><span class="sxs-lookup"><span data-stu-id="5b8b3-124">Element</span></span>|<span data-ttu-id="5b8b3-125">描述</span><span class="sxs-lookup"><span data-stu-id="5b8b3-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5b8b3-126">EnumerableExpansion 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5b8b3-126">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="5b8b3-127">定義當特定 .NET 集合物件顯示在視圖中時，如何展開這些物件。</span><span class="sxs-lookup"><span data-stu-id="5b8b3-127">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5b8b3-128">備註</span><span class="sxs-lookup"><span data-stu-id="5b8b3-128">Remarks</span></span>

<span data-ttu-id="5b8b3-129">您必須為定義專案指定至少一個類型、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="5b8b3-129">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="5b8b3-130">您可以使用的子項目數目沒有最大限制。</span><span class="sxs-lookup"><span data-stu-id="5b8b3-130">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="5b8b3-131">選取條件是用來定義必須存在才能使用定義的條件，例如，當物件具有特定屬性或特定屬性值或腳本評估為時 `true` 。</span><span class="sxs-lookup"><span data-stu-id="5b8b3-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="5b8b3-132">如需選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5b8b3-132">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5b8b3-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b8b3-133">See Also</span></span>

[<span data-ttu-id="5b8b3-134">定義用於顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="5b8b3-134">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="5b8b3-135">EnumerableExpansion 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5b8b3-135">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="5b8b3-136">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5b8b3-136">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="5b8b3-137">EnumerableExpansion 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5b8b3-137">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="5b8b3-138">EnumerableExpansion 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5b8b3-138">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="5b8b3-139">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="5b8b3-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
