---
title: EnumerableExpansion 的之 entryselectedby 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368797"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="c119c-102">EnumerableExpansion 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c119c-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="c119c-103">定義使用此定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="c119c-103">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="c119c-104">EnumerableExpansion 的設定元素（格式） DefaultSettings 元素（格式） EnumerableExpansions 元素（格式） EnumerableExpansion 元素（格式）之 entryselectedby 元素</span><span class="sxs-lookup"><span data-stu-id="c119c-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c119c-105">語法</span><span class="sxs-lookup"><span data-stu-id="c119c-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c119c-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="c119c-106">Attributes and Elements</span></span>

<span data-ttu-id="c119c-107">下列各節說明屬性、子專案，以及 `EntrySelectedBy` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="c119c-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c119c-108">屬性</span><span class="sxs-lookup"><span data-stu-id="c119c-108">Attributes</span></span>

<span data-ttu-id="c119c-109">無。</span><span class="sxs-lookup"><span data-stu-id="c119c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c119c-110">子元素</span><span class="sxs-lookup"><span data-stu-id="c119c-110">Child Elements</span></span>

|<span data-ttu-id="c119c-111">元素</span><span class="sxs-lookup"><span data-stu-id="c119c-111">Element</span></span>|<span data-ttu-id="c119c-112">描述</span><span class="sxs-lookup"><span data-stu-id="c119c-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c119c-113">EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c119c-113">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="c119c-114">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="c119c-114">Optional element.</span></span><br /><br /> <span data-ttu-id="c119c-115">定義必須存在的條件，才能展開這個定義的集合物件。</span><span class="sxs-lookup"><span data-stu-id="c119c-115">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="c119c-116">EnumerableExpansion 之之 entryselectedby 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c119c-116">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="c119c-117">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="c119c-117">Optional element.</span></span><br /><br /> <span data-ttu-id="c119c-118">指定一組 .NET 類型，使用此定義來擴充集合物件的方式。</span><span class="sxs-lookup"><span data-stu-id="c119c-118">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="c119c-119">EnumerableExpansion 之之 entryselectedby 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c119c-119">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="c119c-120">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="c119c-120">Optional element.</span></span><br /><br /> <span data-ttu-id="c119c-121">指定 .NET 類型，其使用此定義來擴充集合物件的方式。</span><span class="sxs-lookup"><span data-stu-id="c119c-121">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c119c-122">父元素</span><span class="sxs-lookup"><span data-stu-id="c119c-122">Parent Elements</span></span>

|<span data-ttu-id="c119c-123">元素</span><span class="sxs-lookup"><span data-stu-id="c119c-123">Element</span></span>|<span data-ttu-id="c119c-124">描述</span><span class="sxs-lookup"><span data-stu-id="c119c-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c119c-125">EnumerableExpansion 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c119c-125">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="c119c-126">定義特定 .NET 集合物件在視圖中顯示時的擴充方式。</span><span class="sxs-lookup"><span data-stu-id="c119c-126">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c119c-127">備註</span><span class="sxs-lookup"><span data-stu-id="c119c-127">Remarks</span></span>

<span data-ttu-id="c119c-128">您必須為定義專案指定至少一個類型、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="c119c-128">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="c119c-129">您可以使用的子項目數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="c119c-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="c119c-130">選取條件是用來定義要使用的定義必須存在的條件，例如，當物件具有特定屬性，或特定屬性值或腳本評估為 `true` 時。</span><span class="sxs-lookup"><span data-stu-id="c119c-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="c119c-131">如需選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c119c-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c119c-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c119c-132">See Also</span></span>

[<span data-ttu-id="c119c-133">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="c119c-133">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c119c-134">EnumerableExpansion 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c119c-134">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="c119c-135">EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c119c-135">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="c119c-136">EnumerableExpansion 之之 entryselectedby 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c119c-136">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="c119c-137">EnumerableExpansion 之之 entryselectedby 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c119c-137">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="c119c-138">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="c119c-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
