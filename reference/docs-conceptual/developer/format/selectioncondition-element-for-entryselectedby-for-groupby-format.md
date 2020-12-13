---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)
description: GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)
ms.openlocfilehash: 14c293b6bc6d6accc201de35be9219349079801d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664753"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="fa481-103">GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fa481-103">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="fa481-104">定義必須存在才能使用控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="fa481-104">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="fa481-105">定義如何顯示新的物件群組時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="fa481-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="fa481-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 專案 (格式) GroupBy 專案的視圖 (格式) CustomEntries 元素適用于 GroupBy (格式) CustomEntry 專案用於 CustomControl 的 groupby (格式) 之 entryselectedby 專案適用于 CustomEntry 的 groupby (格式)  (</span><span class="sxs-lookup"><span data-stu-id="fa481-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fa481-107">語法</span><span class="sxs-lookup"><span data-stu-id="fa481-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fa481-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fa481-108">Attributes and Elements</span></span>

<span data-ttu-id="fa481-109">下列各節說明屬性、子專案和元素的父元素 `SelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="fa481-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fa481-110">屬性</span><span class="sxs-lookup"><span data-stu-id="fa481-110">Attributes</span></span>

<span data-ttu-id="fa481-111">無。</span><span class="sxs-lookup"><span data-stu-id="fa481-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fa481-112">子元素</span><span class="sxs-lookup"><span data-stu-id="fa481-112">Child Elements</span></span>

|<span data-ttu-id="fa481-113">元素</span><span class="sxs-lookup"><span data-stu-id="fa481-113">Element</span></span>|<span data-ttu-id="fa481-114">描述</span><span class="sxs-lookup"><span data-stu-id="fa481-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fa481-115">GroupBy 之 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fa481-115">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="fa481-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="fa481-116">Optional element.</span></span><br /><br /> <span data-ttu-id="fa481-117">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="fa481-117">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="fa481-118">GroupBy (格式的 SelectionCondition 的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="fa481-118">ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="fa481-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="fa481-119">Optional element.</span></span><br /><br /> <span data-ttu-id="fa481-120">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="fa481-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="fa481-121">GroupBy 之 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fa481-121">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="fa481-122">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="fa481-122">Optional element.</span></span><br /><br /> <span data-ttu-id="fa481-123">指定一組觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="fa481-123">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="fa481-124">GroupBy (格式的 SelectionCondition TypeName 元素) </span><span class="sxs-lookup"><span data-stu-id="fa481-124">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="fa481-125">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="fa481-125">Optional element.</span></span><br /><br /> <span data-ttu-id="fa481-126">指定觸發條件的 .NET 型別。</span><span class="sxs-lookup"><span data-stu-id="fa481-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fa481-127">父項目</span><span class="sxs-lookup"><span data-stu-id="fa481-127">Parent Elements</span></span>

|<span data-ttu-id="fa481-128">元素</span><span class="sxs-lookup"><span data-stu-id="fa481-128">Element</span></span>|<span data-ttu-id="fa481-129">描述</span><span class="sxs-lookup"><span data-stu-id="fa481-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fa481-130">GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fa481-130">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="fa481-131">定義使用此控制項定義的 .NET 型別，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="fa481-131">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fa481-132">備註</span><span class="sxs-lookup"><span data-stu-id="fa481-132">Remarks</span></span>

<span data-ttu-id="fa481-133">當您定義選取條件時，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="fa481-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="fa481-134">選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="fa481-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="fa481-135">選取條件可以指定任意數目的 .NET 類型或選取集，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="fa481-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="fa481-136">如需如何使用選取條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="fa481-136">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fa481-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa481-137">See Also</span></span>

[<span data-ttu-id="fa481-138">檢視之 CustomControl 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fa481-138">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="fa481-139">檢視之 CustomControl 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fa481-139">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="fa481-140">View (Format) 的自訂控制項之 SelectionCondition 的 SelectionSetName 元素 </span><span class="sxs-lookup"><span data-stu-id="fa481-140">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="fa481-141">GroupBy (格式的 SelectionCondition TypeName 元素) </span><span class="sxs-lookup"><span data-stu-id="fa481-141">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="fa481-142">GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fa481-142">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="fa481-143">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="fa481-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
