---
title: TableControl 之之 entryselectedby 的 SelectionCondition 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368387"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="a6f00-102">TableControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a6f00-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="a6f00-103">定義必須存在的條件，才能用於這個資料表視圖定義。</span><span class="sxs-lookup"><span data-stu-id="a6f00-103">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="a6f00-104">可以針對資料表定義指定的選取條件數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="a6f00-104">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="a6f00-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（格式）之 entryselectedby 元素（格式）TableRowEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6f00-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a6f00-106">語法</span><span class="sxs-lookup"><span data-stu-id="a6f00-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a6f00-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="a6f00-107">Attributes and Elements</span></span>

<span data-ttu-id="a6f00-108">下列各節說明屬性、子專案，以及 SelectionCondition 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="a6f00-108">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a6f00-109">屬性</span><span class="sxs-lookup"><span data-stu-id="a6f00-109">Attributes</span></span>

<span data-ttu-id="a6f00-110">無。</span><span class="sxs-lookup"><span data-stu-id="a6f00-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a6f00-111">子元素</span><span class="sxs-lookup"><span data-stu-id="a6f00-111">Child Elements</span></span>

|<span data-ttu-id="a6f00-112">元素</span><span class="sxs-lookup"><span data-stu-id="a6f00-112">Element</span></span>|<span data-ttu-id="a6f00-113">描述</span><span class="sxs-lookup"><span data-stu-id="a6f00-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a6f00-114">TableRowEntry 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6f00-114">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="a6f00-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="a6f00-115">Optional element.</span></span><br /><br /> <span data-ttu-id="a6f00-116">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="a6f00-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="a6f00-117">TableRowEntry 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6f00-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="a6f00-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="a6f00-118">Optional element.</span></span><br /><br /> <span data-ttu-id="a6f00-119">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="a6f00-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="a6f00-120">TableRowEntry 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6f00-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="a6f00-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="a6f00-121">Optional element.</span></span><br /><br /> <span data-ttu-id="a6f00-122">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="a6f00-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="a6f00-123">TableRowEntry 之之 entryselectedby 的 SelectionCondition 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6f00-123">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="a6f00-124">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="a6f00-124">Optional element.</span></span><br /><br /> <span data-ttu-id="a6f00-125">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="a6f00-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a6f00-126">父元素</span><span class="sxs-lookup"><span data-stu-id="a6f00-126">Parent Elements</span></span>

|<span data-ttu-id="a6f00-127">元素</span><span class="sxs-lookup"><span data-stu-id="a6f00-127">Element</span></span>|<span data-ttu-id="a6f00-128">描述</span><span class="sxs-lookup"><span data-stu-id="a6f00-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a6f00-129">TableRowEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6f00-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="a6f00-130">定義使用此資料表專案的 .NET 類型，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="a6f00-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a6f00-131">備註</span><span class="sxs-lookup"><span data-stu-id="a6f00-131">Remarks</span></span>

<span data-ttu-id="a6f00-132">每個清單專案都必須定義至少一個型別名稱、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="a6f00-132">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="a6f00-133">當您定義選取條件時，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="a6f00-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="a6f00-134">選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="a6f00-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="a6f00-135">選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="a6f00-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="a6f00-136">如需如何使用選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a6f00-136">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a6f00-137">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="a6f00-137">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a6f00-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6f00-138">See Also</span></span>

[<span data-ttu-id="a6f00-139">建立資料表視圖</span><span class="sxs-lookup"><span data-stu-id="a6f00-139">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a6f00-140">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="a6f00-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a6f00-141">之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6f00-141">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="a6f00-142">TableRowEntry 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6f00-142">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="a6f00-143">TableRowEntry 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6f00-143">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a6f00-144">TableRowEntry 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6f00-144">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a6f00-145">TableRowEntry 之之 entryselectedby 的 SelectionCondition 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6f00-145">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a6f00-146">撰寫 Windows PowerShell 格式化和類型檔案</span><span class="sxs-lookup"><span data-stu-id="a6f00-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
