---
title: View 之控制項的之 entryselectedby 的 SelectionCondition 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362047"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="f927b-102">檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="f927b-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="f927b-103">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="f927b-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="f927b-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="f927b-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="f927b-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素CustomControl for view （format） CustomEntry 元素的 CustomEntries for view （format）之 entryselectedby 元素 for CustomEntry for view （format） SelectionCondition 元素 for controls 的控制項（格式）編排</span><span class="sxs-lookup"><span data-stu-id="f927b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f927b-106">語法</span><span class="sxs-lookup"><span data-stu-id="f927b-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f927b-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="f927b-107">Attributes and Elements</span></span>

<span data-ttu-id="f927b-108">下列各節說明屬性、子專案，以及 `SelectionCondition` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="f927b-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f927b-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f927b-109">Attributes</span></span>

<span data-ttu-id="f927b-110">無。</span><span class="sxs-lookup"><span data-stu-id="f927b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f927b-111">子元素</span><span class="sxs-lookup"><span data-stu-id="f927b-111">Child Elements</span></span>

|<span data-ttu-id="f927b-112">元素</span><span class="sxs-lookup"><span data-stu-id="f927b-112">Element</span></span>|<span data-ttu-id="f927b-113">描述</span><span class="sxs-lookup"><span data-stu-id="f927b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f927b-114">View 之控制項的 SelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f927b-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f927b-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f927b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f927b-116">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="f927b-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f927b-117">View 之控制項的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f927b-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f927b-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f927b-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f927b-119">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="f927b-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="f927b-120">View 之控制項的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f927b-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f927b-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f927b-121">Optional element.</span></span><br /><br /> <span data-ttu-id="f927b-122">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="f927b-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="f927b-123">View 之控制項的 SelectionCondition 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f927b-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f927b-124">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f927b-124">Optional element.</span></span><br /><br /> <span data-ttu-id="f927b-125">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="f927b-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f927b-126">父元素</span><span class="sxs-lookup"><span data-stu-id="f927b-126">Parent Elements</span></span>

|<span data-ttu-id="f927b-127">元素</span><span class="sxs-lookup"><span data-stu-id="f927b-127">Element</span></span>|<span data-ttu-id="f927b-128">描述</span><span class="sxs-lookup"><span data-stu-id="f927b-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f927b-129">View 之控制項的 CustomEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f927b-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="f927b-130">定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="f927b-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f927b-131">備註</span><span class="sxs-lookup"><span data-stu-id="f927b-131">Remarks</span></span>

<span data-ttu-id="f927b-132">當您定義選取條件時，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="f927b-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="f927b-133">選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="f927b-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="f927b-134">選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="f927b-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="f927b-135">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f927b-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f927b-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f927b-136">See Also</span></span>

[<span data-ttu-id="f927b-137">View 之控制項的 SelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f927b-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f927b-138">View 之控制項的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f927b-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f927b-139">View 之控制項的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f927b-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f927b-140">View 之控制項的 SelectionCondition 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f927b-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f927b-141">View 之控制項的 CustomEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f927b-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="f927b-142">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="f927b-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
