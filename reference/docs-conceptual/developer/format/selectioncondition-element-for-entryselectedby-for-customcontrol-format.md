---
title: CustomControl 之之 entryselectedby 的 SelectionCondition 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368437"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="90759-102">CustomControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="90759-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="90759-103">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="90759-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="90759-104">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="90759-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="90759-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素 for view （format） CustomEntries 元素 for CustomEntry for view （format） CustomEntries 元素Format） CustomItem 元素，用於 CustomControl for view （format）之 entryselectedby 元素 CustomEntry for CustomControl for view （format） SelectionCondition 元素之 entryselectedby for view （格式）</span><span class="sxs-lookup"><span data-stu-id="90759-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="90759-106">語法</span><span class="sxs-lookup"><span data-stu-id="90759-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="90759-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="90759-107">Attributes and Elements</span></span>

<span data-ttu-id="90759-108">下列各節說明屬性、子專案，以及 `SelectionCondition` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="90759-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="90759-109">屬性</span><span class="sxs-lookup"><span data-stu-id="90759-109">Attributes</span></span>

<span data-ttu-id="90759-110">無。</span><span class="sxs-lookup"><span data-stu-id="90759-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="90759-111">子元素</span><span class="sxs-lookup"><span data-stu-id="90759-111">Child Elements</span></span>

|<span data-ttu-id="90759-112">元素</span><span class="sxs-lookup"><span data-stu-id="90759-112">Element</span></span>|<span data-ttu-id="90759-113">描述</span><span class="sxs-lookup"><span data-stu-id="90759-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="90759-114">SelectionCondition for CustomControl for View 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="90759-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="90759-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="90759-115">Optional element.</span></span><br /><br /> <span data-ttu-id="90759-116">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="90759-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="90759-117">SelectionCondition for CustomControl for View 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="90759-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="90759-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="90759-118">Optional element.</span></span><br /><br /> <span data-ttu-id="90759-119">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="90759-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="90759-120">View 的自訂控制項的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="90759-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="90759-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="90759-121">Optional element.</span></span><br /><br /> <span data-ttu-id="90759-122">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="90759-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="90759-123">SelectionCondition for CustomControl for View 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="90759-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="90759-124">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="90759-124">Optional element.</span></span><br /><br /> <span data-ttu-id="90759-125">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="90759-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="90759-126">父元素</span><span class="sxs-lookup"><span data-stu-id="90759-126">Parent Elements</span></span>

|<span data-ttu-id="90759-127">元素</span><span class="sxs-lookup"><span data-stu-id="90759-127">Element</span></span>|<span data-ttu-id="90759-128">描述</span><span class="sxs-lookup"><span data-stu-id="90759-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="90759-129">CustomControl for View 的 CustomEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="90759-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="90759-130">定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="90759-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="90759-131">備註</span><span class="sxs-lookup"><span data-stu-id="90759-131">Remarks</span></span>

<span data-ttu-id="90759-132">當您定義選取條件時，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="90759-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="90759-133">選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="90759-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="90759-134">選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="90759-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="90759-135">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="90759-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="90759-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90759-136">See Also</span></span>

[<span data-ttu-id="90759-137">SelectionCondition for CustomControl for View 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="90759-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="90759-138">SelectionCondition for CustomControl for View 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="90759-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="90759-139">View 的自訂控制項的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="90759-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="90759-140">SelectionCondition for CustomControl for View 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="90759-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="90759-141">CustomControl for View 的 CustomEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="90759-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="90759-142">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="90759-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
