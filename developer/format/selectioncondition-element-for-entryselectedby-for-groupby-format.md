---
title: GroupBy （格式） 的 EntrySelectedBy SelectionCondition 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855164"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="552f9-102">GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="552f9-102">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="552f9-103">定義必須存在於要使用的控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="552f9-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="552f9-104">定義新的群組物件的顯示方式時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="552f9-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="552f9-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素CustomControl CustomEntry EntrySelectedBy 的 GroupBy （格式） 的 GroupBy （格式） SelectionCondition 元素的 GroupBy （格式） EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="552f9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="552f9-106">語法</span><span class="sxs-lookup"><span data-stu-id="552f9-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="552f9-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="552f9-107">Attributes and Elements</span></span>

<span data-ttu-id="552f9-108">下列各節說明屬性、 子項目和父項目`SelectionCondition`項目。</span><span class="sxs-lookup"><span data-stu-id="552f9-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="552f9-109">屬性</span><span class="sxs-lookup"><span data-stu-id="552f9-109">Attributes</span></span>

<span data-ttu-id="552f9-110">無。</span><span class="sxs-lookup"><span data-stu-id="552f9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="552f9-111">子元素</span><span class="sxs-lookup"><span data-stu-id="552f9-111">Child Elements</span></span>

|<span data-ttu-id="552f9-112">元素</span><span class="sxs-lookup"><span data-stu-id="552f9-112">Element</span></span>|<span data-ttu-id="552f9-113">描述</span><span class="sxs-lookup"><span data-stu-id="552f9-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="552f9-114">PropertyName SelectionCondition 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="552f9-114">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="552f9-115">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="552f9-115">Optional element.</span></span><br /><br /> <span data-ttu-id="552f9-116">指定觸發條件的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="552f9-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="552f9-117">GroupBy （格式） 的 SelectionCondition 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="552f9-117">ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="552f9-118">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="552f9-118">Optional element.</span></span><br /><br /> <span data-ttu-id="552f9-119">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="552f9-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="552f9-120">GroupBy （格式） 的 SelectionCondition SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="552f9-120">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="552f9-121">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="552f9-121">Optional element.</span></span><br /><br /> <span data-ttu-id="552f9-122">指定觸發條件的.NET 型別集。</span><span class="sxs-lookup"><span data-stu-id="552f9-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="552f9-123">GroupBy （格式） 的 SelectionCondition TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="552f9-123">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="552f9-124">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="552f9-124">Optional element.</span></span><br /><br /> <span data-ttu-id="552f9-125">指定觸發條件的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="552f9-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="552f9-126">父元素</span><span class="sxs-lookup"><span data-stu-id="552f9-126">Parent Elements</span></span>

|<span data-ttu-id="552f9-127">元素</span><span class="sxs-lookup"><span data-stu-id="552f9-127">Element</span></span>|<span data-ttu-id="552f9-128">描述</span><span class="sxs-lookup"><span data-stu-id="552f9-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="552f9-129">GroupBy （格式） 的 CustomEntry EntrySelectedBy 項目</span><span class="sxs-lookup"><span data-stu-id="552f9-129">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="552f9-130">定義使用此控制項定義或必須存在於要使用此定義條件的.NET 類型。</span><span class="sxs-lookup"><span data-stu-id="552f9-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="552f9-131">備註</span><span class="sxs-lookup"><span data-stu-id="552f9-131">Remarks</span></span>

<span data-ttu-id="552f9-132">在您定義的選取範圍條件時，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="552f9-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="552f9-133">選取條件必須指定至少一個屬性名稱或指令碼區塊，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="552f9-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="552f9-134">選取條件可以指定任意數目的.NET 型別，或選取項目集，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="552f9-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="552f9-135">如需如何使用選擇條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="552f9-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="552f9-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="552f9-136">See Also</span></span>

[<span data-ttu-id="552f9-137">PropertyName SelectionCondition 如 CustomControl 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="552f9-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="552f9-138">SelectionCondition CustomControl 檢視 （格式） 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="552f9-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="552f9-139">SelectionSetName SelectionCondition 檢視 （格式） 的自訂控制項的項目</span><span class="sxs-lookup"><span data-stu-id="552f9-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="552f9-140">GroupBy （格式） 的 SelectionCondition TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="552f9-140">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="552f9-141">GroupBy （格式） 的 CustomEntry EntrySelectedBy 項目</span><span class="sxs-lookup"><span data-stu-id="552f9-141">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="552f9-142">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="552f9-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
