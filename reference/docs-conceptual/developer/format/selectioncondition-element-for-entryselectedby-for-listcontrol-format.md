---
title: ListControl 之之 entryselectedby 的 SelectionCondition 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: 7150b29ad84dfb587215ee3e64c356adbd5a6305
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417549"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="f92b9-102">ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="f92b9-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="f92b9-103">定義必須存在才能使用此清單視圖定義的條件。</span><span class="sxs-lookup"><span data-stu-id="f92b9-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="f92b9-104">可以為清單定義指定的選取條件數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="f92b9-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="f92b9-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（格式） ListEntries 元素（格式） ListEntry 元素（格式）之 entryselectedby 元素（代表的 ListEntry （格式） SelectionCondition 元素）ListEntry 的之 entryselectedby （格式）</span><span class="sxs-lookup"><span data-stu-id="f92b9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f92b9-106">語法</span><span class="sxs-lookup"><span data-stu-id="f92b9-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f92b9-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="f92b9-107">Attributes and Elements</span></span>

<span data-ttu-id="f92b9-108">下列各節說明屬性、子專案，以及 `SelectionCondition` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="f92b9-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f92b9-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f92b9-109">Attributes</span></span>

<span data-ttu-id="f92b9-110">無。</span><span class="sxs-lookup"><span data-stu-id="f92b9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f92b9-111">子元素</span><span class="sxs-lookup"><span data-stu-id="f92b9-111">Child Elements</span></span>

|<span data-ttu-id="f92b9-112">元素</span><span class="sxs-lookup"><span data-stu-id="f92b9-112">Element</span></span>|<span data-ttu-id="f92b9-113">說明</span><span class="sxs-lookup"><span data-stu-id="f92b9-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f92b9-114">ListEntry 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f92b9-114">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="f92b9-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f92b9-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f92b9-116">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="f92b9-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f92b9-117">ListEntry 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f92b9-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="f92b9-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f92b9-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f92b9-119">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="f92b9-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="f92b9-120">ListEntry 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f92b9-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="f92b9-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f92b9-121">Optional element.</span></span><br /><br /> <span data-ttu-id="f92b9-122">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="f92b9-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="f92b9-123">ListEntry 之之 entryselectedby 的 SelectionCondition 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f92b9-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="f92b9-124">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f92b9-124">Optional element.</span></span><br /><br /> <span data-ttu-id="f92b9-125">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="f92b9-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f92b9-126">父元素</span><span class="sxs-lookup"><span data-stu-id="f92b9-126">Parent Elements</span></span>

|<span data-ttu-id="f92b9-127">元素</span><span class="sxs-lookup"><span data-stu-id="f92b9-127">Element</span></span>|<span data-ttu-id="f92b9-128">說明</span><span class="sxs-lookup"><span data-stu-id="f92b9-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f92b9-129">TableRowEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f92b9-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="f92b9-130">定義使用此資料表專案的 .NET 類型，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="f92b9-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f92b9-131">備註</span><span class="sxs-lookup"><span data-stu-id="f92b9-131">Remarks</span></span>

<span data-ttu-id="f92b9-132">lWhen 您定義選取條件時，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="f92b9-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="f92b9-133">選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="f92b9-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="f92b9-134">選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="f92b9-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="f92b9-135">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f92b9-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f92b9-136">如需清單視圖之其他元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="f92b9-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f92b9-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f92b9-137">See Also</span></span>

[<span data-ttu-id="f92b9-138">建立清單視圖</span><span class="sxs-lookup"><span data-stu-id="f92b9-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f92b9-139">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="f92b9-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f92b9-140">ListEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f92b9-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="f92b9-141">ListEntry 之之 entryselectedby 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f92b9-141">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="f92b9-142">ListEntry 之之 entryselectedby 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f92b9-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](/powershell/scripting/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[<span data-ttu-id="f92b9-143">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="f92b9-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
