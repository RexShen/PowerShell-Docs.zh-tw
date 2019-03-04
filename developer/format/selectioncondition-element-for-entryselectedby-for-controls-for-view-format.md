---
title: 用於檢視 （格式） 的控制項 EntrySelectedBy SelectionCondition 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858014"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="0334b-102">檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0334b-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="0334b-103">定義必須存在，要使用的控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="0334b-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="0334b-104">定義可供檢視的控制項時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="0334b-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="0334b-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目CustomControl CustomEntries CustomEntry EntrySelectedBy 的檢視 （控制項的檢視 （格式） SelectionCondition 元素的控制項的檢視 （格式） EntrySelectedBy 元素的控制項的檢視 （格式） CustomEntry 元素的控制項格式）</span><span class="sxs-lookup"><span data-stu-id="0334b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0334b-106">語法</span><span class="sxs-lookup"><span data-stu-id="0334b-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0334b-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="0334b-107">Attributes and Elements</span></span>

<span data-ttu-id="0334b-108">下列各節說明屬性、 子項目和父項目`SelectionCondition`項目。</span><span class="sxs-lookup"><span data-stu-id="0334b-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0334b-109">屬性</span><span class="sxs-lookup"><span data-stu-id="0334b-109">Attributes</span></span>

<span data-ttu-id="0334b-110">無。</span><span class="sxs-lookup"><span data-stu-id="0334b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0334b-111">子元素</span><span class="sxs-lookup"><span data-stu-id="0334b-111">Child Elements</span></span>

|<span data-ttu-id="0334b-112">元素</span><span class="sxs-lookup"><span data-stu-id="0334b-112">Element</span></span>|<span data-ttu-id="0334b-113">描述</span><span class="sxs-lookup"><span data-stu-id="0334b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0334b-114">PropertyName SelectionCondition 用於檢視 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="0334b-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="0334b-115">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="0334b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="0334b-116">指定觸發條件的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="0334b-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="0334b-117">用於檢視 （格式） 的控制項 SelectionCondition 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="0334b-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="0334b-118">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="0334b-118">Optional element.</span></span><br /><br /> <span data-ttu-id="0334b-119">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="0334b-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="0334b-120">用於檢視 （格式） 的控制項 SelectionCondition SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="0334b-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="0334b-121">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="0334b-121">Optional element.</span></span><br /><br /> <span data-ttu-id="0334b-122">指定觸發條件的.NET 型別集。</span><span class="sxs-lookup"><span data-stu-id="0334b-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="0334b-123">用於檢視 （格式） 的控制項 SelectionCondition TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="0334b-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="0334b-124">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="0334b-124">Optional element.</span></span><br /><br /> <span data-ttu-id="0334b-125">指定觸發條件的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="0334b-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0334b-126">父元素</span><span class="sxs-lookup"><span data-stu-id="0334b-126">Parent Elements</span></span>

|<span data-ttu-id="0334b-127">元素</span><span class="sxs-lookup"><span data-stu-id="0334b-127">Element</span></span>|<span data-ttu-id="0334b-128">描述</span><span class="sxs-lookup"><span data-stu-id="0334b-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0334b-129">用於檢視 （格式） 的控制項 CustomEntry EntrySelectedBy 項目</span><span class="sxs-lookup"><span data-stu-id="0334b-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="0334b-130">定義使用此控制項定義或必須存在於要使用此定義條件的.NET 類型。</span><span class="sxs-lookup"><span data-stu-id="0334b-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0334b-131">備註</span><span class="sxs-lookup"><span data-stu-id="0334b-131">Remarks</span></span>

<span data-ttu-id="0334b-132">在您定義的選取範圍條件時，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="0334b-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="0334b-133">選取條件必須指定至少一個屬性名稱或指令碼區塊，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="0334b-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="0334b-134">選取條件可以指定任意數目的.NET 型別，或選取項目集，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="0334b-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="0334b-135">如需如何使用選擇條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="0334b-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0334b-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0334b-136">See Also</span></span>

[<span data-ttu-id="0334b-137">PropertyName SelectionCondition 用於檢視 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="0334b-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="0334b-138">用於檢視 （格式） 的控制項 SelectionCondition 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="0334b-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="0334b-139">用於檢視 （格式） 的控制項 SelectionCondition SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="0334b-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="0334b-140">用於檢視 （格式） 的控制項 SelectionCondition TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="0334b-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="0334b-141">用於檢視 （格式） 的控制項 CustomEntry EntrySelectedBy 項目</span><span class="sxs-lookup"><span data-stu-id="0334b-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="0334b-142">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="0334b-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
