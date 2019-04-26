---
title: TableControl （格式） 的 EntrySelectedBy SelectionCondition 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075659"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="224f6-102">TableControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="224f6-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="224f6-103">定義要用於此 [資料表] 檢視的定義必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="224f6-103">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="224f6-104">選取範圍可以針對資料表定義指定的條件數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="224f6-104">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="224f6-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 （格式） TableRowEntry 項目 （格式） EntrySelectedBy 項目 TableRowEntry （格式）TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="224f6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="224f6-106">語法</span><span class="sxs-lookup"><span data-stu-id="224f6-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="224f6-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="224f6-107">Attributes and Elements</span></span>

<span data-ttu-id="224f6-108">下列各節說明屬性、 子項目和 SelectionCondition 元素的父項目。</span><span class="sxs-lookup"><span data-stu-id="224f6-108">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="224f6-109">屬性</span><span class="sxs-lookup"><span data-stu-id="224f6-109">Attributes</span></span>

<span data-ttu-id="224f6-110">無。</span><span class="sxs-lookup"><span data-stu-id="224f6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="224f6-111">子元素</span><span class="sxs-lookup"><span data-stu-id="224f6-111">Child Elements</span></span>

|<span data-ttu-id="224f6-112">元素</span><span class="sxs-lookup"><span data-stu-id="224f6-112">Element</span></span>|<span data-ttu-id="224f6-113">描述</span><span class="sxs-lookup"><span data-stu-id="224f6-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="224f6-114">PropertyName TableRowEntry （格式） 的 EntrySelectedBy 的 SelectionCondition 的項目</span><span class="sxs-lookup"><span data-stu-id="224f6-114">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="224f6-115">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="224f6-115">Optional element.</span></span><br /><br /> <span data-ttu-id="224f6-116">指定觸發條件的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="224f6-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="224f6-117">針對 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="224f6-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="224f6-118">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="224f6-118">Optional element.</span></span><br /><br /> <span data-ttu-id="224f6-119">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="224f6-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="224f6-120">針對 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="224f6-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="224f6-121">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="224f6-121">Optional element.</span></span><br /><br /> <span data-ttu-id="224f6-122">指定的觸發條件的.NET 型別集。</span><span class="sxs-lookup"><span data-stu-id="224f6-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="224f6-123">針對 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="224f6-123">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="224f6-124">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="224f6-124">Optional element.</span></span><br /><br /> <span data-ttu-id="224f6-125">指定觸發條件的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="224f6-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="224f6-126">父項目</span><span class="sxs-lookup"><span data-stu-id="224f6-126">Parent Elements</span></span>

|<span data-ttu-id="224f6-127">項目</span><span class="sxs-lookup"><span data-stu-id="224f6-127">Element</span></span>|<span data-ttu-id="224f6-128">描述</span><span class="sxs-lookup"><span data-stu-id="224f6-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="224f6-129">EntrySelectedBy TableRowEntry （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="224f6-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="224f6-130">定義.NET 型別，使用此資料表項目或要使用此項目必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="224f6-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="224f6-131">備註</span><span class="sxs-lookup"><span data-stu-id="224f6-131">Remarks</span></span>

<span data-ttu-id="224f6-132">每個清單項目必須至少一個型別名稱、 選取項目集或選擇條件的定義。</span><span class="sxs-lookup"><span data-stu-id="224f6-132">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="224f6-133">在您定義的選取範圍條件時，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="224f6-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="224f6-134">選取條件必須指定至少一個屬性名稱或指令碼區塊，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="224f6-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="224f6-135">選取條件可以指定任意數目的.NET 型別，或選取項目集，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="224f6-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="224f6-136">如需如何使用選擇條件的詳細資訊，請參閱[定義條件時檢視項目或項目用](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="224f6-136">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="224f6-137">資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="224f6-137">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="224f6-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="224f6-138">See Also</span></span>

[<span data-ttu-id="224f6-139">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="224f6-139">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="224f6-140">定義何時顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="224f6-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="224f6-141">EntrySelectedBy 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="224f6-141">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="224f6-142">PropertyName TableRowEntry （格式） 的 EntrySelectedBy 的 SelectionCondition 的項目</span><span class="sxs-lookup"><span data-stu-id="224f6-142">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="224f6-143">針對 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="224f6-143">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="224f6-144">針對 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="224f6-144">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="224f6-145">針對 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="224f6-145">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="224f6-146">撰寫 Windows PowerShell 格式和類型的檔案</span><span class="sxs-lookup"><span data-stu-id="224f6-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
