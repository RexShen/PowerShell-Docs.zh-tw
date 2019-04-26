---
title: ListControl （格式） 的 ListEntry EntrySelectedBy 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066187"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="fb0e0-102">ListControl 之 ListEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fb0e0-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="fb0e0-103">定義.NET 型別，使用這個清單檢視的定義或必須存在於要使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="fb0e0-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="fb0e0-104">在大部分情況下只有一個定義所需的清單檢視。</span><span class="sxs-lookup"><span data-stu-id="fb0e0-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="fb0e0-105">不過，您可以提供多個定義清單檢視，如果您想要使用相同的清單檢視來顯示不同的資料，針對不同物件中。</span><span class="sxs-lookup"><span data-stu-id="fb0e0-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="fb0e0-106">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目用於 ListControl （格式） EntrySelectedBy 元素 ListEntry ListControl （格式） ListEntry 項目ListControl （格式） 的 ListEntry</span><span class="sxs-lookup"><span data-stu-id="fb0e0-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fb0e0-107">語法</span><span class="sxs-lookup"><span data-stu-id="fb0e0-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fb0e0-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fb0e0-108">Attributes and Elements</span></span>

<span data-ttu-id="fb0e0-109">下列各節說明屬性、 子項目和父項目`EntrySelectedBy`項目。</span><span class="sxs-lookup"><span data-stu-id="fb0e0-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fb0e0-110">屬性</span><span class="sxs-lookup"><span data-stu-id="fb0e0-110">Attributes</span></span>

<span data-ttu-id="fb0e0-111">無。</span><span class="sxs-lookup"><span data-stu-id="fb0e0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fb0e0-112">子元素</span><span class="sxs-lookup"><span data-stu-id="fb0e0-112">Child Elements</span></span>

|<span data-ttu-id="fb0e0-113">元素</span><span class="sxs-lookup"><span data-stu-id="fb0e0-113">Element</span></span>|<span data-ttu-id="fb0e0-114">描述</span><span class="sxs-lookup"><span data-stu-id="fb0e0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fb0e0-115">ListControl （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="fb0e0-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="fb0e0-116">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="fb0e0-116">Optional element.</span></span><br /><br /> <span data-ttu-id="fb0e0-117">定義要使用此清單檢視定義必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="fb0e0-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="fb0e0-118">ListControl （格式） 的 EntrySelectedBy SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="fb0e0-118">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="fb0e0-119">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="fb0e0-119">Optional element.</span></span><br /><br /> <span data-ttu-id="fb0e0-120">指定一組使用此清單檢視定義的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="fb0e0-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="fb0e0-121">ListControl （格式） 的 EntrySelectedBy TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="fb0e0-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="fb0e0-122">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="fb0e0-122">Optional element.</span></span><br /><br /> <span data-ttu-id="fb0e0-123">指定使用此清單的檢視定義的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="fb0e0-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fb0e0-124">父項目</span><span class="sxs-lookup"><span data-stu-id="fb0e0-124">Parent Elements</span></span>

|<span data-ttu-id="fb0e0-125">項目</span><span class="sxs-lookup"><span data-stu-id="fb0e0-125">Element</span></span>|<span data-ttu-id="fb0e0-126">描述</span><span class="sxs-lookup"><span data-stu-id="fb0e0-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fb0e0-127">ListEntry ListControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="fb0e0-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="fb0e0-128">定義清單的資料列的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="fb0e0-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fb0e0-129">備註</span><span class="sxs-lookup"><span data-stu-id="fb0e0-129">Remarks</span></span>

<span data-ttu-id="fb0e0-130">您必須指定至少一個型別、 選取項目集或選取項目在清單檢視定義的條件。</span><span class="sxs-lookup"><span data-stu-id="fb0e0-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="fb0e0-131">沒有任何子項目的，您可以使用數字的最大限制。</span><span class="sxs-lookup"><span data-stu-id="fb0e0-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="fb0e0-132">選擇條件用來定義要使用，例如當物件具有特定屬性的定義必須存在的條件，或特定的屬性值或指令碼會評估為`true`。</span><span class="sxs-lookup"><span data-stu-id="fb0e0-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="fb0e0-133">如需有關選擇條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="fb0e0-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="fb0e0-134">清單檢視元件的相關資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="fb0e0-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fb0e0-135">範例</span><span class="sxs-lookup"><span data-stu-id="fb0e0-135">Example</span></span>

<span data-ttu-id="fb0e0-136">下列範例示範如何定義使用他們的.NET 型別名稱的清單檢視的物件。</span><span class="sxs-lookup"><span data-stu-id="fb0e0-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="fb0e0-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb0e0-137">See Also</span></span>

[<span data-ttu-id="fb0e0-138">ListEntry ListControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="fb0e0-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="fb0e0-139">ListControl （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="fb0e0-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="fb0e0-140">ListControl （格式） 的 EntrySelectedBy SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="fb0e0-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="fb0e0-141">ListControl （格式） 的 EntrySelectedBy TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="fb0e0-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="fb0e0-142">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="fb0e0-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="fb0e0-143">定義何時顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="fb0e0-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="fb0e0-144">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="fb0e0-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
