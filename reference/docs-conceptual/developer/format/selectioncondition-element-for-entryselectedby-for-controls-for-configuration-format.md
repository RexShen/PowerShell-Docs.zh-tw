---
title: 設定之控制項的之 entryselectedby 的 SelectionCondition 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368447"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="55111-102">設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="55111-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="55111-103">定義必須存在的條件，才能使用通用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="55111-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="55111-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="55111-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="55111-105">Configuration 元素（格式）控制項的設定（格式）控制項元素的元素，用於控制項的設定（format） CustomControl 元素，用於控制項的 CustomControl 的設定（格式） CustomEntries 元素設定（格式） CustomEntry 元素，用於 CustomControl 的設定（格式）之 entryselectedby 元素（適用于 SelectionCondition for 之 entryselectedby 的設定（Format） CustomEntry 元素）之控制項的 CustomEntry設定（格式）</span><span class="sxs-lookup"><span data-stu-id="55111-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="55111-106">語法</span><span class="sxs-lookup"><span data-stu-id="55111-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="55111-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="55111-107">Attributes and Elements</span></span>

<span data-ttu-id="55111-108">下列各節說明屬性、子專案，以及 `SelectionCondition` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="55111-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="55111-109">屬性</span><span class="sxs-lookup"><span data-stu-id="55111-109">Attributes</span></span>

<span data-ttu-id="55111-110">無。</span><span class="sxs-lookup"><span data-stu-id="55111-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="55111-111">子元素</span><span class="sxs-lookup"><span data-stu-id="55111-111">Child Elements</span></span>

|<span data-ttu-id="55111-112">元素</span><span class="sxs-lookup"><span data-stu-id="55111-112">Element</span></span>|<span data-ttu-id="55111-113">描述</span><span class="sxs-lookup"><span data-stu-id="55111-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="55111-114">設定之控制項的 SelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="55111-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="55111-115">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="55111-115">Optional element.</span></span><br /><br /> <span data-ttu-id="55111-116">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="55111-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="55111-117">設定之控制項的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="55111-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="55111-118">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="55111-118">Optional element.</span></span><br /><br /> <span data-ttu-id="55111-119">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="55111-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="55111-120">設定之控制項的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="55111-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="55111-121">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="55111-121">Optional element.</span></span><br /><br /> <span data-ttu-id="55111-122">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="55111-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="55111-123">設定之控制項的 SelectionCondition 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="55111-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="55111-124">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="55111-124">Optional element.</span></span><br /><br /> <span data-ttu-id="55111-125">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="55111-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="55111-126">父元素</span><span class="sxs-lookup"><span data-stu-id="55111-126">Parent Elements</span></span>

|<span data-ttu-id="55111-127">元素</span><span class="sxs-lookup"><span data-stu-id="55111-127">Element</span></span>|<span data-ttu-id="55111-128">描述</span><span class="sxs-lookup"><span data-stu-id="55111-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="55111-129">設定之控制項的 CustomEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="55111-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="55111-130">定義使用此通用控制項定義之專案的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="55111-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="55111-131">備註</span><span class="sxs-lookup"><span data-stu-id="55111-131">Remarks</span></span>

<span data-ttu-id="55111-132">定義選取條件時，必須遵循下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="55111-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="55111-133">選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="55111-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="55111-134">選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="55111-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="55111-135">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="55111-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="55111-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55111-136">See Also</span></span>

[<span data-ttu-id="55111-137">設定之控制項的 SelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="55111-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="55111-138">設定之控制項的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="55111-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="55111-139">設定之控制項的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="55111-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="55111-140">設定之控制項的 SelectionCondition 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="55111-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="55111-141">設定之控制項的 CustomEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="55111-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="55111-142">撰寫 Windows PowerShell 格式化和類型檔案</span><span class="sxs-lookup"><span data-stu-id="55111-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
