---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)
description: ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)
ms.openlocfilehash: e93499691dd0046265e43abd26497b2974546083
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655095"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="f855e-103">ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="f855e-103">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="f855e-104">定義必須存在的條件，才能使用此清單視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="f855e-104">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="f855e-105">可以針對清單定義指定的選取條件數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="f855e-105">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="f855e-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 元素 (格式) ListEntries 元素 (格式) ListEntry 專案 (格式) 之 entryselectedby 專案 (格式) ListEntry 專案 SelectionCondition 的之 entryselectedby (格式) </span><span class="sxs-lookup"><span data-stu-id="f855e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f855e-107">語法</span><span class="sxs-lookup"><span data-stu-id="f855e-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f855e-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f855e-108">Attributes and Elements</span></span>

<span data-ttu-id="f855e-109">下列各節說明屬性、子專案和元素的父元素 `SelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="f855e-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f855e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f855e-110">Attributes</span></span>

<span data-ttu-id="f855e-111">無。</span><span class="sxs-lookup"><span data-stu-id="f855e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f855e-112">子元素</span><span class="sxs-lookup"><span data-stu-id="f855e-112">Child Elements</span></span>

|<span data-ttu-id="f855e-113">元素</span><span class="sxs-lookup"><span data-stu-id="f855e-113">Element</span></span>|<span data-ttu-id="f855e-114">描述</span><span class="sxs-lookup"><span data-stu-id="f855e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f855e-115">ListEntry (格式之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素) </span><span class="sxs-lookup"><span data-stu-id="f855e-115">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="f855e-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f855e-116">Optional element.</span></span><br /><br /> <span data-ttu-id="f855e-117">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="f855e-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f855e-118">適用于 ListEntry (格式之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="f855e-118">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="f855e-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f855e-119">Optional element.</span></span><br /><br /> <span data-ttu-id="f855e-120">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="f855e-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="f855e-121">ListEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="f855e-121">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="f855e-122">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f855e-122">Optional element.</span></span><br /><br /> <span data-ttu-id="f855e-123">指定一組觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="f855e-123">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="f855e-124">ListEntry (格式之之 entryselectedby 的 SelectionCondition 的 TypeName 元素) </span><span class="sxs-lookup"><span data-stu-id="f855e-124">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="f855e-125">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f855e-125">Optional element.</span></span><br /><br /> <span data-ttu-id="f855e-126">指定觸發條件的 .NET 型別。</span><span class="sxs-lookup"><span data-stu-id="f855e-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f855e-127">父項目</span><span class="sxs-lookup"><span data-stu-id="f855e-127">Parent Elements</span></span>

|<span data-ttu-id="f855e-128">元素</span><span class="sxs-lookup"><span data-stu-id="f855e-128">Element</span></span>|<span data-ttu-id="f855e-129">描述</span><span class="sxs-lookup"><span data-stu-id="f855e-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f855e-130">TableRowEntry (格式的之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="f855e-130">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="f855e-131">定義使用此資料表專案的 .NET 型別，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="f855e-131">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f855e-132">備註</span><span class="sxs-lookup"><span data-stu-id="f855e-132">Remarks</span></span>

<span data-ttu-id="f855e-133">lWhen 您正在定義選取條件，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="f855e-133">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="f855e-134">選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="f855e-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="f855e-135">選取條件可以指定任意數目的 .NET 類型或選取集，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="f855e-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="f855e-136">如需如何使用選取條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f855e-136">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f855e-137">如需清單視圖之其他元件的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="f855e-137">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f855e-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f855e-138">See Also</span></span>

[<span data-ttu-id="f855e-139">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="f855e-139">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f855e-140">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="f855e-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f855e-141">ListEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="f855e-141">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="f855e-142">適用于之 entryselectedby 的 ListEntry (格式的 SelectionSetName 元素) </span><span class="sxs-lookup"><span data-stu-id="f855e-142">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="f855e-143">適用于 ListEntry 的之 entryselectedby 的 TypeName 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="f855e-143">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](/powershell/scripting/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[<span data-ttu-id="f855e-144">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="f855e-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
