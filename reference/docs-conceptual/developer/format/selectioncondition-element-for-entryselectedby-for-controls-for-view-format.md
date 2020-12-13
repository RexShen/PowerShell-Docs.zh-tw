---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)
description: 檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)
ms.openlocfilehash: 16b048e73195b3d6168724714ff223851dc1b20b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664859"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="c580f-103">檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c580f-103">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="c580f-104">定義必須存在才能使用控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="c580f-104">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="c580f-105">當定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="c580f-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="c580f-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 專案 (格式) 控制項專案 (格式) 控制項專案 (格式控制項的控制項) 格式 (CustomEntries 元素 view (格式的控制項 CustomControl) CustomEntry 專案的 CustomEntries 控制項，適用于 view 的格式) 之 entryselectedby (格式的控制項) 格式 (CustomEntry 專案) 格式的控制項 (</span><span class="sxs-lookup"><span data-stu-id="c580f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c580f-107">語法</span><span class="sxs-lookup"><span data-stu-id="c580f-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c580f-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c580f-108">Attributes and Elements</span></span>

<span data-ttu-id="c580f-109">下列各節說明屬性、子專案和元素的父元素 `SelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="c580f-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c580f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c580f-110">Attributes</span></span>

<span data-ttu-id="c580f-111">無。</span><span class="sxs-lookup"><span data-stu-id="c580f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c580f-112">子元素</span><span class="sxs-lookup"><span data-stu-id="c580f-112">Child Elements</span></span>

|<span data-ttu-id="c580f-113">元素</span><span class="sxs-lookup"><span data-stu-id="c580f-113">Element</span></span>|<span data-ttu-id="c580f-114">描述</span><span class="sxs-lookup"><span data-stu-id="c580f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c580f-115">檢視之控制項的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c580f-115">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="c580f-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="c580f-116">Optional element.</span></span><br /><br /> <span data-ttu-id="c580f-117">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="c580f-117">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="c580f-118">檢視之控制項的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c580f-118">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="c580f-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="c580f-119">Optional element.</span></span><br /><br /> <span data-ttu-id="c580f-120">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="c580f-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="c580f-121">檢視之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c580f-121">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="c580f-122">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="c580f-122">Optional element.</span></span><br /><br /> <span data-ttu-id="c580f-123">指定一組觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="c580f-123">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="c580f-124">檢視之控制項的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c580f-124">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="c580f-125">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="c580f-125">Optional element.</span></span><br /><br /> <span data-ttu-id="c580f-126">指定觸發條件的 .NET 型別。</span><span class="sxs-lookup"><span data-stu-id="c580f-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c580f-127">父項目</span><span class="sxs-lookup"><span data-stu-id="c580f-127">Parent Elements</span></span>

|<span data-ttu-id="c580f-128">元素</span><span class="sxs-lookup"><span data-stu-id="c580f-128">Element</span></span>|<span data-ttu-id="c580f-129">描述</span><span class="sxs-lookup"><span data-stu-id="c580f-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c580f-130">檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c580f-130">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="c580f-131">定義使用此控制項定義的 .NET 型別，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="c580f-131">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c580f-132">備註</span><span class="sxs-lookup"><span data-stu-id="c580f-132">Remarks</span></span>

<span data-ttu-id="c580f-133">當您定義選取條件時，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="c580f-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="c580f-134">選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="c580f-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="c580f-135">選取條件可以指定任意數目的 .NET 類型或選取集，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="c580f-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="c580f-136">如需如何使用選取條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c580f-136">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c580f-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c580f-137">See Also</span></span>

[<span data-ttu-id="c580f-138">檢視之控制項的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c580f-138">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="c580f-139">檢視之控制項的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c580f-139">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="c580f-140">檢視之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c580f-140">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="c580f-141">檢視之控制項的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c580f-141">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="c580f-142">檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c580f-142">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="c580f-143">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="c580f-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
