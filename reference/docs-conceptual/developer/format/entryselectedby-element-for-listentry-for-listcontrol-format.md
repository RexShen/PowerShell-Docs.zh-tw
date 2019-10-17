---
title: ListControl 之 ListEntry 的之 entryselectedby 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363827"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="c6e62-102">ListControl 之 ListEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c6e62-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="c6e62-103">定義使用此清單視圖定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="c6e62-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="c6e62-104">在大部分情況下，清單視圖只需要一個定義。</span><span class="sxs-lookup"><span data-stu-id="c6e62-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="c6e62-105">不過，如果您想要使用相同的清單視圖來顯示不同物件的不同資料，可以為清單視圖提供多個定義。</span><span class="sxs-lookup"><span data-stu-id="c6e62-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="c6e62-106">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（format） ListEntries 元素，用於 ListEntry for ListEntry （Format） ListControl 元素的 ListControl （Format）之 entryselectedby 元素ListControl 的 ListEntry （格式）</span><span class="sxs-lookup"><span data-stu-id="c6e62-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c6e62-107">語法</span><span class="sxs-lookup"><span data-stu-id="c6e62-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c6e62-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="c6e62-108">Attributes and Elements</span></span>

<span data-ttu-id="c6e62-109">下列各節說明屬性、子專案，以及 `EntrySelectedBy` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="c6e62-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c6e62-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c6e62-110">Attributes</span></span>

<span data-ttu-id="c6e62-111">無。</span><span class="sxs-lookup"><span data-stu-id="c6e62-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c6e62-112">子元素</span><span class="sxs-lookup"><span data-stu-id="c6e62-112">Child Elements</span></span>

|<span data-ttu-id="c6e62-113">元素</span><span class="sxs-lookup"><span data-stu-id="c6e62-113">Element</span></span>|<span data-ttu-id="c6e62-114">描述</span><span class="sxs-lookup"><span data-stu-id="c6e62-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c6e62-115">ListControl 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c6e62-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="c6e62-116">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="c6e62-116">Optional element.</span></span><br /><br /> <span data-ttu-id="c6e62-117">定義必須存在才能使用此清單視圖定義的條件。</span><span class="sxs-lookup"><span data-stu-id="c6e62-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="c6e62-118">ListControl 之之 entryselectedby 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c6e62-118">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="c6e62-119">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="c6e62-119">Optional element.</span></span><br /><br /> <span data-ttu-id="c6e62-120">指定一組使用此清單視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="c6e62-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="c6e62-121">ListControl 之之 entryselectedby 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c6e62-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="c6e62-122">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="c6e62-122">Optional element.</span></span><br /><br /> <span data-ttu-id="c6e62-123">指定使用此清單視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="c6e62-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c6e62-124">父元素</span><span class="sxs-lookup"><span data-stu-id="c6e62-124">Parent Elements</span></span>

|<span data-ttu-id="c6e62-125">元素</span><span class="sxs-lookup"><span data-stu-id="c6e62-125">Element</span></span>|<span data-ttu-id="c6e62-126">描述</span><span class="sxs-lookup"><span data-stu-id="c6e62-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c6e62-127">ListControl 的 ListEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c6e62-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="c6e62-128">定義清單資料列的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="c6e62-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c6e62-129">備註</span><span class="sxs-lookup"><span data-stu-id="c6e62-129">Remarks</span></span>

<span data-ttu-id="c6e62-130">您必須為清單視圖定義指定至少一個類型、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="c6e62-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="c6e62-131">您可以使用的子項目數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="c6e62-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="c6e62-132">選取條件是用來定義要使用的定義必須存在的條件，例如，當物件具有特定屬性，或特定屬性值或腳本評估為 `true` 時。</span><span class="sxs-lookup"><span data-stu-id="c6e62-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="c6e62-133">如需選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c6e62-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="c6e62-134">如需清單視圖之元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="c6e62-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c6e62-135">範例</span><span class="sxs-lookup"><span data-stu-id="c6e62-135">Example</span></span>

<span data-ttu-id="c6e62-136">下列範例顯示如何使用 .NET 型別名稱來定義清單視圖的物件。</span><span class="sxs-lookup"><span data-stu-id="c6e62-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="c6e62-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6e62-137">See Also</span></span>

[<span data-ttu-id="c6e62-138">ListControl 的 ListEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c6e62-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="c6e62-139">ListControl 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c6e62-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="c6e62-140">ListControl 之之 entryselectedby 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c6e62-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="c6e62-141">ListControl 之之 entryselectedby 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c6e62-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="c6e62-142">建立清單視圖</span><span class="sxs-lookup"><span data-stu-id="c6e62-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c6e62-143">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="c6e62-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c6e62-144">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="c6e62-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)