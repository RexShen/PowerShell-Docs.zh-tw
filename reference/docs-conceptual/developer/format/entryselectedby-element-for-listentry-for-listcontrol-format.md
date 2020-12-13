---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 ListEntry 的 EntrySelectedBy 元素 (格式)
description: ListControl 之 ListEntry 的 EntrySelectedBy 元素 (格式)
ms.openlocfilehash: 1981c8fae65f494504d6cdd9f59337d555350b07
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652282"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="63be2-103">ListControl 之 ListEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="63be2-103">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="63be2-104">定義使用此清單視圖定義或必須存在才能使用此定義之條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="63be2-104">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="63be2-105">在大部分情況下，清單視圖只需要一個定義。</span><span class="sxs-lookup"><span data-stu-id="63be2-105">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="63be2-106">但是，如果您想要使用相同的清單視圖來顯示不同物件的不同資料，則可以為清單視圖提供多個定義。</span><span class="sxs-lookup"><span data-stu-id="63be2-106">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="63be2-107">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 元素 (format) ListEntries 元素 for ListControl (Format) ListEntry ListEntry for ListControl for 之 entryselectedby (ListEntry for ListControl for) format (</span><span class="sxs-lookup"><span data-stu-id="63be2-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="63be2-108">語法</span><span class="sxs-lookup"><span data-stu-id="63be2-108">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="63be2-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="63be2-109">Attributes and Elements</span></span>

<span data-ttu-id="63be2-110">下列章節說明屬性、子專案和元素的父元素 `EntrySelectedBy` 。</span><span class="sxs-lookup"><span data-stu-id="63be2-110">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="63be2-111">屬性</span><span class="sxs-lookup"><span data-stu-id="63be2-111">Attributes</span></span>

<span data-ttu-id="63be2-112">無。</span><span class="sxs-lookup"><span data-stu-id="63be2-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="63be2-113">子元素</span><span class="sxs-lookup"><span data-stu-id="63be2-113">Child Elements</span></span>

|<span data-ttu-id="63be2-114">元素</span><span class="sxs-lookup"><span data-stu-id="63be2-114">Element</span></span>|<span data-ttu-id="63be2-115">描述</span><span class="sxs-lookup"><span data-stu-id="63be2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="63be2-116">適用于之 entryselectedby 的 ListControl (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="63be2-116">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="63be2-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="63be2-117">Optional element.</span></span><br /><br /> <span data-ttu-id="63be2-118">定義必須存在的條件，才能使用此清單視圖定義。</span><span class="sxs-lookup"><span data-stu-id="63be2-118">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="63be2-119">ListControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="63be2-119">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="63be2-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="63be2-120">Optional element.</span></span><br /><br /> <span data-ttu-id="63be2-121">指定一組使用此清單視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="63be2-121">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="63be2-122">ListControl 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="63be2-122">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="63be2-123">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="63be2-123">Optional element.</span></span><br /><br /> <span data-ttu-id="63be2-124">指定使用此清單視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="63be2-124">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="63be2-125">父項目</span><span class="sxs-lookup"><span data-stu-id="63be2-125">Parent Elements</span></span>

|<span data-ttu-id="63be2-126">元素</span><span class="sxs-lookup"><span data-stu-id="63be2-126">Element</span></span>|<span data-ttu-id="63be2-127">描述</span><span class="sxs-lookup"><span data-stu-id="63be2-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="63be2-128">ListControl 的 ListEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="63be2-128">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="63be2-129">定義如何顯示清單的資料列。</span><span class="sxs-lookup"><span data-stu-id="63be2-129">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="63be2-130">備註</span><span class="sxs-lookup"><span data-stu-id="63be2-130">Remarks</span></span>

<span data-ttu-id="63be2-131">您必須為清單視圖定義指定至少一個類型、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="63be2-131">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="63be2-132">您可以使用的子項目數目沒有最大限制。</span><span class="sxs-lookup"><span data-stu-id="63be2-132">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="63be2-133">選取條件是用來定義必須存在才能使用定義的條件，例如，當物件具有特定屬性或特定屬性值或腳本評估為時 `true` 。</span><span class="sxs-lookup"><span data-stu-id="63be2-133">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="63be2-134">如需選取條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="63be2-134">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="63be2-135">如需清單視圖元件的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="63be2-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="63be2-136">範例</span><span class="sxs-lookup"><span data-stu-id="63be2-136">Example</span></span>

<span data-ttu-id="63be2-137">下列範例示範如何使用 .NET 型別名稱定義清單視圖的物件。</span><span class="sxs-lookup"><span data-stu-id="63be2-137">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="63be2-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63be2-138">See Also</span></span>

[<span data-ttu-id="63be2-139">ListControl 的 ListEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="63be2-139">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="63be2-140">ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="63be2-140">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="63be2-141">ListControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="63be2-141">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="63be2-142">ListControl 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="63be2-142">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="63be2-143">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="63be2-143">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="63be2-144">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="63be2-144">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="63be2-145">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="63be2-145">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
