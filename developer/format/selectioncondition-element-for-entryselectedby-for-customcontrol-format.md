---
title: CustomControl （格式） 的 EntrySelectedBy SelectionCondition 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858824"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="5ecdc-102">CustomControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5ecdc-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="5ecdc-103">定義必須存在於要使用的控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="5ecdc-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="5ecdc-104">定義自訂控制項的檢視時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="5ecdc-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="5ecdc-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目進行檢視 （格式） 的檢視 （如 CustomControl CustomEntries CustomEntry 元素 CustomControl 的檢視 （格式） CustomEntries 項目格式） 的檢視 （格式） EntrySelectedBy 項目，如 CustomControl EntrySelectedBy CustomControl 檢視 （格式） 的檢視 （格式） SelectionCondition 元素的 CustomEntry CustomControl CustomEntry CustomItem 項目</span><span class="sxs-lookup"><span data-stu-id="5ecdc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5ecdc-106">語法</span><span class="sxs-lookup"><span data-stu-id="5ecdc-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5ecdc-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="5ecdc-107">Attributes and Elements</span></span>

<span data-ttu-id="5ecdc-108">下列各節說明屬性、 子項目和父項目`SelectionCondition`項目。</span><span class="sxs-lookup"><span data-stu-id="5ecdc-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5ecdc-109">屬性</span><span class="sxs-lookup"><span data-stu-id="5ecdc-109">Attributes</span></span>

<span data-ttu-id="5ecdc-110">無。</span><span class="sxs-lookup"><span data-stu-id="5ecdc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5ecdc-111">子元素</span><span class="sxs-lookup"><span data-stu-id="5ecdc-111">Child Elements</span></span>

|<span data-ttu-id="5ecdc-112">元素</span><span class="sxs-lookup"><span data-stu-id="5ecdc-112">Element</span></span>|<span data-ttu-id="5ecdc-113">描述</span><span class="sxs-lookup"><span data-stu-id="5ecdc-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ecdc-114">PropertyName SelectionCondition 如 CustomControl 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="5ecdc-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="5ecdc-115">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="5ecdc-115">Optional element.</span></span><br /><br /> <span data-ttu-id="5ecdc-116">指定觸發條件的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="5ecdc-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="5ecdc-117">SelectionCondition CustomControl 檢視 （格式） 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="5ecdc-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="5ecdc-118">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="5ecdc-118">Optional element.</span></span><br /><br /> <span data-ttu-id="5ecdc-119">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="5ecdc-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="5ecdc-120">SelectionSetName SelectionCondition 檢視 （格式） 的自訂控制項的項目</span><span class="sxs-lookup"><span data-stu-id="5ecdc-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="5ecdc-121">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="5ecdc-121">Optional element.</span></span><br /><br /> <span data-ttu-id="5ecdc-122">指定觸發條件的.NET 型別集。</span><span class="sxs-lookup"><span data-stu-id="5ecdc-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="5ecdc-123">CustomControl 檢視 （格式） 的 SelectionCondition TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="5ecdc-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="5ecdc-124">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="5ecdc-124">Optional element.</span></span><br /><br /> <span data-ttu-id="5ecdc-125">指定觸發條件的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="5ecdc-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5ecdc-126">父元素</span><span class="sxs-lookup"><span data-stu-id="5ecdc-126">Parent Elements</span></span>

|<span data-ttu-id="5ecdc-127">元素</span><span class="sxs-lookup"><span data-stu-id="5ecdc-127">Element</span></span>|<span data-ttu-id="5ecdc-128">描述</span><span class="sxs-lookup"><span data-stu-id="5ecdc-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ecdc-129">CustomControl 檢視 （格式） 的 CustomEntry EntrySelectedBy 項目</span><span class="sxs-lookup"><span data-stu-id="5ecdc-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="5ecdc-130">定義使用此控制項定義或必須存在於要使用此定義條件的.NET 類型。</span><span class="sxs-lookup"><span data-stu-id="5ecdc-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5ecdc-131">備註</span><span class="sxs-lookup"><span data-stu-id="5ecdc-131">Remarks</span></span>

<span data-ttu-id="5ecdc-132">在您定義的選取範圍條件時，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="5ecdc-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="5ecdc-133">選取條件必須指定至少一個屬性名稱或指令碼區塊，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="5ecdc-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="5ecdc-134">選取條件可以指定任意數目的.NET 型別，或選取項目集，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="5ecdc-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="5ecdc-135">如需如何使用選擇條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5ecdc-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5ecdc-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ecdc-136">See Also</span></span>

[<span data-ttu-id="5ecdc-137">PropertyName SelectionCondition 如 CustomControl 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="5ecdc-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5ecdc-138">SelectionCondition CustomControl 檢視 （格式） 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="5ecdc-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5ecdc-139">SelectionSetName SelectionCondition 檢視 （格式） 的自訂控制項的項目</span><span class="sxs-lookup"><span data-stu-id="5ecdc-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5ecdc-140">CustomControl 檢視 （格式） 的 SelectionCondition TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="5ecdc-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5ecdc-141">CustomControl 檢視 （格式） 的 CustomEntry EntrySelectedBy 項目</span><span class="sxs-lookup"><span data-stu-id="5ecdc-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5ecdc-142">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="5ecdc-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
