---
title: EntrySelectedBy EnumerableExpansion （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066204"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="0dc02-102">EnumerableExpansion 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0dc02-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="0dc02-103">定義.NET 類型使用這個定義或必須存在於要使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="0dc02-103">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="0dc02-104">組態項目 （格式） DefaultSettings 項目 （格式） EnumerableExpansions 項目 （格式） EnumerableExpansion 項目 （格式） EntrySelectedBy 項目 EnumerableExpansion （格式）</span><span class="sxs-lookup"><span data-stu-id="0dc02-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0dc02-105">語法</span><span class="sxs-lookup"><span data-stu-id="0dc02-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0dc02-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0dc02-106">Attributes and Elements</span></span>

<span data-ttu-id="0dc02-107">下列各節說明屬性、 子項目和父項目`EntrySelectedBy`項目。</span><span class="sxs-lookup"><span data-stu-id="0dc02-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0dc02-108">屬性</span><span class="sxs-lookup"><span data-stu-id="0dc02-108">Attributes</span></span>

<span data-ttu-id="0dc02-109">無。</span><span class="sxs-lookup"><span data-stu-id="0dc02-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0dc02-110">子元素</span><span class="sxs-lookup"><span data-stu-id="0dc02-110">Child Elements</span></span>

|<span data-ttu-id="0dc02-111">元素</span><span class="sxs-lookup"><span data-stu-id="0dc02-111">Element</span></span>|<span data-ttu-id="0dc02-112">描述</span><span class="sxs-lookup"><span data-stu-id="0dc02-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0dc02-113">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="0dc02-113">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="0dc02-114">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="0dc02-114">Optional element.</span></span><br /><br /> <span data-ttu-id="0dc02-115">定義必須存在以展開此定義的集合物件的條件。</span><span class="sxs-lookup"><span data-stu-id="0dc02-115">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="0dc02-116">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="0dc02-116">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="0dc02-117">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="0dc02-117">Optional element.</span></span><br /><br /> <span data-ttu-id="0dc02-118">指定一組.NET 型別，使用此定義的集合物件擴充的方式。</span><span class="sxs-lookup"><span data-stu-id="0dc02-118">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="0dc02-119">EnumerableExpansion （格式） 的 EntrySelectedBy TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="0dc02-119">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="0dc02-120">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="0dc02-120">Optional element.</span></span><br /><br /> <span data-ttu-id="0dc02-121">指定的.NET 型別會使用這個定義的集合物件擴充的方式。</span><span class="sxs-lookup"><span data-stu-id="0dc02-121">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0dc02-122">父項目</span><span class="sxs-lookup"><span data-stu-id="0dc02-122">Parent Elements</span></span>

|<span data-ttu-id="0dc02-123">項目</span><span class="sxs-lookup"><span data-stu-id="0dc02-123">Element</span></span>|<span data-ttu-id="0dc02-124">描述</span><span class="sxs-lookup"><span data-stu-id="0dc02-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0dc02-125">EnumerableExpansion 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="0dc02-125">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="0dc02-126">定義在檢視中顯示時，會展開物件的特定.NET 集合。</span><span class="sxs-lookup"><span data-stu-id="0dc02-126">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0dc02-127">備註</span><span class="sxs-lookup"><span data-stu-id="0dc02-127">Remarks</span></span>

<span data-ttu-id="0dc02-128">您必須指定至少一個型別、 選取項目集或選擇條件的定義項目。</span><span class="sxs-lookup"><span data-stu-id="0dc02-128">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="0dc02-129">沒有任何子項目的，您可以使用數字的最大限制。</span><span class="sxs-lookup"><span data-stu-id="0dc02-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="0dc02-130">選擇條件用來定義要使用，例如當物件具有特定屬性的定義必須存在的條件，或特定的屬性值或指令碼會評估為`true`。</span><span class="sxs-lookup"><span data-stu-id="0dc02-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="0dc02-131">如需有關選擇條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="0dc02-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0dc02-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0dc02-132">See Also</span></span>

[<span data-ttu-id="0dc02-133">定義用於顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="0dc02-133">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="0dc02-134">EnumerableExpansion 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="0dc02-134">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="0dc02-135">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="0dc02-135">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="0dc02-136">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="0dc02-136">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="0dc02-137">EnumerableExpansion （格式） 的 EntrySelectedBy TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="0dc02-137">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="0dc02-138">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="0dc02-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
