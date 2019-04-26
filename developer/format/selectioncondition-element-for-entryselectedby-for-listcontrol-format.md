---
title: ListControl （格式） 的 EntrySelectedBy SelectionCondition 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: 633204f3b181316761746ea2679910216fb74657
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064096"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="331da-102">ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="331da-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="331da-103">定義要使用此清單檢視的定義必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="331da-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="331da-104">選取範圍條件可指定在清單定義的數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="331da-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="331da-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 （格式） ListEntry 項目 （格式） EntrySelectedBy 項目用於 ListEntry （格式） SelectionCondition 元素ListEntry （格式） 的 EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="331da-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="331da-106">語法</span><span class="sxs-lookup"><span data-stu-id="331da-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="331da-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="331da-107">Attributes and Elements</span></span>

<span data-ttu-id="331da-108">下列各節說明屬性、 子項目和父項目`SelectionCondition`項目。</span><span class="sxs-lookup"><span data-stu-id="331da-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="331da-109">屬性</span><span class="sxs-lookup"><span data-stu-id="331da-109">Attributes</span></span>

<span data-ttu-id="331da-110">無。</span><span class="sxs-lookup"><span data-stu-id="331da-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="331da-111">子元素</span><span class="sxs-lookup"><span data-stu-id="331da-111">Child Elements</span></span>

|<span data-ttu-id="331da-112">元素</span><span class="sxs-lookup"><span data-stu-id="331da-112">Element</span></span>|<span data-ttu-id="331da-113">描述</span><span class="sxs-lookup"><span data-stu-id="331da-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="331da-114">PropertyName ListEntry （格式） 的 EntrySelectedBy 的 SelectionCondition 的項目</span><span class="sxs-lookup"><span data-stu-id="331da-114">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="331da-115">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="331da-115">Optional element.</span></span><br /><br /> <span data-ttu-id="331da-116">指定觸發條件的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="331da-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="331da-117">針對 ListEntry （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="331da-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="331da-118">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="331da-118">Optional element.</span></span><br /><br /> <span data-ttu-id="331da-119">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="331da-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="331da-120">針對 ListEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="331da-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="331da-121">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="331da-121">Optional element.</span></span><br /><br /> <span data-ttu-id="331da-122">指定的觸發條件的.NET 型別集。</span><span class="sxs-lookup"><span data-stu-id="331da-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="331da-123">針對 ListEntry （格式） 的 EntrySelectedBy SelectionCondition TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="331da-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="331da-124">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="331da-124">Optional element.</span></span><br /><br /> <span data-ttu-id="331da-125">指定觸發條件的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="331da-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="331da-126">父項目</span><span class="sxs-lookup"><span data-stu-id="331da-126">Parent Elements</span></span>

|<span data-ttu-id="331da-127">項目</span><span class="sxs-lookup"><span data-stu-id="331da-127">Element</span></span>|<span data-ttu-id="331da-128">描述</span><span class="sxs-lookup"><span data-stu-id="331da-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="331da-129">EntrySelectedBy TableRowEntry （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="331da-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="331da-130">定義.NET 型別，使用此資料表項目或要使用此項目必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="331da-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="331da-131">備註</span><span class="sxs-lookup"><span data-stu-id="331da-131">Remarks</span></span>

<span data-ttu-id="331da-132">您正在定義的選取範圍條件 lWhen，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="331da-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="331da-133">選取條件必須指定至少一個屬性名稱或指令碼區塊，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="331da-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="331da-134">選取條件可以指定任意數目的.NET 型別，或選取項目集，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="331da-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="331da-135">如需如何使用選擇條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="331da-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="331da-136">清單檢視的其他元件的相關資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="331da-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="331da-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="331da-137">See Also</span></span>

[<span data-ttu-id="331da-138">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="331da-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="331da-139">定義何時顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="331da-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="331da-140">ListEntry 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="331da-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="331da-141">ListEntry （格式） 的 EntrySelectedBy SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="331da-141">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="331da-142">ListEntry （格式） 的 EntrySelectedBy TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="331da-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](http://msdn.microsoft.com/en-us/fcd4daa6-f3fd-43f7-a468-03c582d34533)

[<span data-ttu-id="331da-143">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="331da-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
