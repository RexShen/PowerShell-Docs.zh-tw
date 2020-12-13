---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)
description: TableControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)
ms.openlocfilehash: 22f304615c6433ffb67f3b4046b645d0c37be8a4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645762"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="a00d0-103">TableControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a00d0-103">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="a00d0-104">定義必須存在的條件，才能用於此資料表視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="a00d0-104">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="a00d0-105">可以針對資料表定義指定的選取條件數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="a00d0-105">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="a00d0-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) TableControl 元素 (格式) TableRowEntries 元素 (格式) TableRowEntry 專案 (格式) 之 entryselectedby 專案 (格式) TableRowEntry 專案 SelectionCondition 的之 entryselectedby (格式) </span><span class="sxs-lookup"><span data-stu-id="a00d0-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a00d0-107">語法</span><span class="sxs-lookup"><span data-stu-id="a00d0-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a00d0-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a00d0-108">Attributes and Elements</span></span>

<span data-ttu-id="a00d0-109">下列各節說明屬性、子專案，以及 SelectionCondition 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="a00d0-109">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a00d0-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a00d0-110">Attributes</span></span>

<span data-ttu-id="a00d0-111">無。</span><span class="sxs-lookup"><span data-stu-id="a00d0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a00d0-112">子元素</span><span class="sxs-lookup"><span data-stu-id="a00d0-112">Child Elements</span></span>

|<span data-ttu-id="a00d0-113">元素</span><span class="sxs-lookup"><span data-stu-id="a00d0-113">Element</span></span>|<span data-ttu-id="a00d0-114">描述</span><span class="sxs-lookup"><span data-stu-id="a00d0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a00d0-115">TableRowEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a00d0-115">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="a00d0-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="a00d0-116">Optional element.</span></span><br /><br /> <span data-ttu-id="a00d0-117">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="a00d0-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="a00d0-118">適用于 TableRowEntry (格式之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="a00d0-118">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="a00d0-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="a00d0-119">Optional element.</span></span><br /><br /> <span data-ttu-id="a00d0-120">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="a00d0-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="a00d0-121">適用于 TableRowEntry 的之 entryselectedby (格式的 SelectionCondition SelectionSetName 元素) </span><span class="sxs-lookup"><span data-stu-id="a00d0-121">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="a00d0-122">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="a00d0-122">Optional element.</span></span><br /><br /> <span data-ttu-id="a00d0-123">指定一組觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="a00d0-123">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="a00d0-124">TableRowEntry (格式之之 entryselectedby 的 SelectionCondition 的 TypeName 元素) </span><span class="sxs-lookup"><span data-stu-id="a00d0-124">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="a00d0-125">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="a00d0-125">Optional element.</span></span><br /><br /> <span data-ttu-id="a00d0-126">指定觸發條件的 .NET 型別。</span><span class="sxs-lookup"><span data-stu-id="a00d0-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a00d0-127">父項目</span><span class="sxs-lookup"><span data-stu-id="a00d0-127">Parent Elements</span></span>

|<span data-ttu-id="a00d0-128">元素</span><span class="sxs-lookup"><span data-stu-id="a00d0-128">Element</span></span>|<span data-ttu-id="a00d0-129">描述</span><span class="sxs-lookup"><span data-stu-id="a00d0-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a00d0-130">TableRowEntry (格式的之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="a00d0-130">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="a00d0-131">定義使用此資料表專案的 .NET 型別，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="a00d0-131">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a00d0-132">備註</span><span class="sxs-lookup"><span data-stu-id="a00d0-132">Remarks</span></span>

<span data-ttu-id="a00d0-133">每個清單專案都必須定義至少一個類型名稱、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="a00d0-133">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="a00d0-134">當您定義選取條件時，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="a00d0-134">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="a00d0-135">選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="a00d0-135">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="a00d0-136">選取條件可以指定任意數目的 .NET 類型或選取集，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="a00d0-136">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="a00d0-137">如需如何使用選取條件的詳細資訊，請參閱 [定義使用視圖專案或專案的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a00d0-137">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a00d0-138">如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="a00d0-138">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a00d0-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a00d0-139">See Also</span></span>

[<span data-ttu-id="a00d0-140">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="a00d0-140">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a00d0-141">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="a00d0-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a00d0-142">之 entryselectedby 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="a00d0-142">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="a00d0-143">TableRowEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a00d0-143">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="a00d0-144">適用于 TableRowEntry (格式之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="a00d0-144">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a00d0-145">適用于 TableRowEntry 的之 entryselectedby (格式的 SelectionCondition SelectionSetName 元素) </span><span class="sxs-lookup"><span data-stu-id="a00d0-145">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a00d0-146">TableRowEntry (格式之之 entryselectedby 的 SelectionCondition 的 TypeName 元素) </span><span class="sxs-lookup"><span data-stu-id="a00d0-146">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a00d0-147">寫入 Windows PowerShell 格式和類型檔案</span><span class="sxs-lookup"><span data-stu-id="a00d0-147">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
