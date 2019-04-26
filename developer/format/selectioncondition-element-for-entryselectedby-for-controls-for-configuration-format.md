---
title: SelectionCondition EntrySelectedBy 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075761"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="f38d1-102">設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="f38d1-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="f38d1-103">定義必須存在，要使用的通用控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="f38d1-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="f38d1-104">定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="f38d1-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="f38d1-105">組態 （格式） 的組態 （格式） CustomControl 項目控制項的 CustomControl 的組態 （格式） CustomEntries 項目控制項的控制項的控制項項目的組態項目 （格式） 的控制項項目針對 CustomEntry 的 EntrySelectedBy 的組態 （格式） SelectionCondition 項目控制項的 CustomEntry 的組態 （格式） EntrySelectedBy 項目控制項的 CustomControl 的組態 （格式） CustomEntry 項目組態 （格式）</span><span class="sxs-lookup"><span data-stu-id="f38d1-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f38d1-106">語法</span><span class="sxs-lookup"><span data-stu-id="f38d1-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f38d1-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f38d1-107">Attributes and Elements</span></span>

<span data-ttu-id="f38d1-108">下列各節說明屬性、 子項目和父項目`SelectionCondition`項目。</span><span class="sxs-lookup"><span data-stu-id="f38d1-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f38d1-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f38d1-109">Attributes</span></span>

<span data-ttu-id="f38d1-110">無。</span><span class="sxs-lookup"><span data-stu-id="f38d1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f38d1-111">子元素</span><span class="sxs-lookup"><span data-stu-id="f38d1-111">Child Elements</span></span>

|<span data-ttu-id="f38d1-112">元素</span><span class="sxs-lookup"><span data-stu-id="f38d1-112">Element</span></span>|<span data-ttu-id="f38d1-113">描述</span><span class="sxs-lookup"><span data-stu-id="f38d1-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f38d1-114">PropertyName SelectionCondition 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="f38d1-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f38d1-115">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="f38d1-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f38d1-116">指定觸發條件的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="f38d1-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f38d1-117">ScriptBlock SelectionCondition 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="f38d1-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f38d1-118">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="f38d1-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f38d1-119">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="f38d1-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="f38d1-120">SelectionSetName SelectionCondition 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="f38d1-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f38d1-121">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="f38d1-121">Optional element.</span></span><br /><br /> <span data-ttu-id="f38d1-122">指定觸發條件的.NET 型別集。</span><span class="sxs-lookup"><span data-stu-id="f38d1-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="f38d1-123">TypeName SelectionCondition 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="f38d1-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f38d1-124">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="f38d1-124">Optional element.</span></span><br /><br /> <span data-ttu-id="f38d1-125">指定觸發條件的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="f38d1-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f38d1-126">父項目</span><span class="sxs-lookup"><span data-stu-id="f38d1-126">Parent Elements</span></span>

|<span data-ttu-id="f38d1-127">項目</span><span class="sxs-lookup"><span data-stu-id="f38d1-127">Element</span></span>|<span data-ttu-id="f38d1-128">描述</span><span class="sxs-lookup"><span data-stu-id="f38d1-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f38d1-129">EntrySelectedBy CustomEntry 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="f38d1-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="f38d1-130">定義.NET 型別，使用通用控制項定義的這個項目。</span><span class="sxs-lookup"><span data-stu-id="f38d1-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f38d1-131">備註</span><span class="sxs-lookup"><span data-stu-id="f38d1-131">Remarks</span></span>

<span data-ttu-id="f38d1-132">定義選取範圍條件時，必須遵循下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="f38d1-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="f38d1-133">選取條件必須指定至少一個屬性名稱或指令碼區塊，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="f38d1-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="f38d1-134">選取條件可以指定任意數目的.NET 型別，或選取項目集，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="f38d1-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="f38d1-135">如需如何使用選擇條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f38d1-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f38d1-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f38d1-136">See Also</span></span>

[<span data-ttu-id="f38d1-137">PropertyName SelectionCondition 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="f38d1-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f38d1-138">ScriptBlock SelectionCondition 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="f38d1-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f38d1-139">SelectionSetName SelectionCondition 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="f38d1-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f38d1-140">TypeName SelectionCondition 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="f38d1-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f38d1-141">EntrySelectedBy CustomEntry 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="f38d1-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="f38d1-142">撰寫 Windows PowerShell 格式和類型的檔案</span><span class="sxs-lookup"><span data-stu-id="f38d1-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
