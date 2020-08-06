---
title: ListControl (格式) 的 ListEntry 的之 entryselectedby 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d6ab1c08dd353da74d1a7d27c569d2fa86e083c3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774111"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="2c961-102">ListControl 之 ListEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2c961-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="2c961-103">定義使用此清單視圖定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="2c961-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="2c961-104">在大部分情況下，清單視圖只需要一個定義。</span><span class="sxs-lookup"><span data-stu-id="2c961-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="2c961-105">不過，如果您想要使用相同的清單視圖來顯示不同物件的不同資料，可以為清單視圖提供多個定義。</span><span class="sxs-lookup"><span data-stu-id="2c961-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="2c961-106">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListControl (格式) ListEntry 元素，ListEntry 的 ListControl (格式) 之 entryselectedby 元素 (</span><span class="sxs-lookup"><span data-stu-id="2c961-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2c961-107">語法</span><span class="sxs-lookup"><span data-stu-id="2c961-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2c961-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2c961-108">Attributes and Elements</span></span>

<span data-ttu-id="2c961-109">下列各節說明屬性、子專案和元素的父元素 `EntrySelectedBy` 。</span><span class="sxs-lookup"><span data-stu-id="2c961-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2c961-110">屬性</span><span class="sxs-lookup"><span data-stu-id="2c961-110">Attributes</span></span>

<span data-ttu-id="2c961-111">無。</span><span class="sxs-lookup"><span data-stu-id="2c961-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2c961-112">子元素</span><span class="sxs-lookup"><span data-stu-id="2c961-112">Child Elements</span></span>

|<span data-ttu-id="2c961-113">元素</span><span class="sxs-lookup"><span data-stu-id="2c961-113">Element</span></span>|<span data-ttu-id="2c961-114">描述</span><span class="sxs-lookup"><span data-stu-id="2c961-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2c961-115">ListControl (格式的之 entryselectedby 的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="2c961-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="2c961-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="2c961-116">Optional element.</span></span><br /><br /> <span data-ttu-id="2c961-117">定義必須存在才能使用此清單視圖定義的條件。</span><span class="sxs-lookup"><span data-stu-id="2c961-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="2c961-118">ListControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2c961-118">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="2c961-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="2c961-119">Optional element.</span></span><br /><br /> <span data-ttu-id="2c961-120">指定一組使用此清單視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="2c961-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="2c961-121">ListControl 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2c961-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="2c961-122">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="2c961-122">Optional element.</span></span><br /><br /> <span data-ttu-id="2c961-123">指定使用此清單視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="2c961-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2c961-124">父項目</span><span class="sxs-lookup"><span data-stu-id="2c961-124">Parent Elements</span></span>

|<span data-ttu-id="2c961-125">元素</span><span class="sxs-lookup"><span data-stu-id="2c961-125">Element</span></span>|<span data-ttu-id="2c961-126">描述</span><span class="sxs-lookup"><span data-stu-id="2c961-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2c961-127">ListControl 的 ListEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2c961-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="2c961-128">定義清單資料列的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="2c961-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2c961-129">備註</span><span class="sxs-lookup"><span data-stu-id="2c961-129">Remarks</span></span>

<span data-ttu-id="2c961-130">您必須為清單視圖定義指定至少一個類型、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="2c961-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="2c961-131">您可以使用的子項目數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="2c961-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="2c961-132">選取條件是用來定義要使用的定義必須存在的條件，例如，當物件具有特定屬性或特定屬性值或腳本評估為時 `true` 。</span><span class="sxs-lookup"><span data-stu-id="2c961-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="2c961-133">如需選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="2c961-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="2c961-134">如需清單視圖之元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="2c961-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2c961-135">範例</span><span class="sxs-lookup"><span data-stu-id="2c961-135">Example</span></span>

<span data-ttu-id="2c961-136">下列範例顯示如何使用 .NET 型別名稱來定義清單視圖的物件。</span><span class="sxs-lookup"><span data-stu-id="2c961-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="2c961-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c961-137">See Also</span></span>

[<span data-ttu-id="2c961-138">ListControl 的 ListEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2c961-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="2c961-139">ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2c961-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="2c961-140">ListControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2c961-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="2c961-141">ListControl 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2c961-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="2c961-142">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="2c961-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="2c961-143">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="2c961-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2c961-144">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="2c961-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
