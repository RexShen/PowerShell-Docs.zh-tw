---
title: 適用于之 entryselectedby 之 GroupBy (格式的 SelectionCondition 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0930d8076c314c12cac6cdfa2b33716b7efeb6a9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772836"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="a0a6f-102">GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a0a6f-102">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="a0a6f-103">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="a0a6f-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="a0a6f-104">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="a0a6f-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="a0a6f-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素（GroupBy (格式）) CustomEntries 專案（適用于 CustomEntry 的 groupby (格式) CustomControl 專案 (之 entryselectedby 元素（適用于 groupby) 格式的 CustomEntry） (SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="a0a6f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a0a6f-106">語法</span><span class="sxs-lookup"><span data-stu-id="a0a6f-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a0a6f-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a0a6f-107">Attributes and Elements</span></span>

<span data-ttu-id="a0a6f-108">下列各節說明屬性、子專案和元素的父元素 `SelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="a0a6f-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a0a6f-109">屬性</span><span class="sxs-lookup"><span data-stu-id="a0a6f-109">Attributes</span></span>

<span data-ttu-id="a0a6f-110">無。</span><span class="sxs-lookup"><span data-stu-id="a0a6f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a0a6f-111">子元素</span><span class="sxs-lookup"><span data-stu-id="a0a6f-111">Child Elements</span></span>

|<span data-ttu-id="a0a6f-112">元素</span><span class="sxs-lookup"><span data-stu-id="a0a6f-112">Element</span></span>|<span data-ttu-id="a0a6f-113">描述</span><span class="sxs-lookup"><span data-stu-id="a0a6f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a0a6f-114">GroupBy 之 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a0a6f-114">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="a0a6f-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="a0a6f-115">Optional element.</span></span><br /><br /> <span data-ttu-id="a0a6f-116">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="a0a6f-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="a0a6f-117">GroupBy (格式的 SelectionCondition 的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="a0a6f-117">ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="a0a6f-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="a0a6f-118">Optional element.</span></span><br /><br /> <span data-ttu-id="a0a6f-119">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="a0a6f-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="a0a6f-120">GroupBy 之 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a0a6f-120">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="a0a6f-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="a0a6f-121">Optional element.</span></span><br /><br /> <span data-ttu-id="a0a6f-122">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="a0a6f-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="a0a6f-123">GroupBy (格式的 SelectionCondition 的 TypeName 元素) </span><span class="sxs-lookup"><span data-stu-id="a0a6f-123">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="a0a6f-124">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="a0a6f-124">Optional element.</span></span><br /><br /> <span data-ttu-id="a0a6f-125">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="a0a6f-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a0a6f-126">父項目</span><span class="sxs-lookup"><span data-stu-id="a0a6f-126">Parent Elements</span></span>

|<span data-ttu-id="a0a6f-127">元素</span><span class="sxs-lookup"><span data-stu-id="a0a6f-127">Element</span></span>|<span data-ttu-id="a0a6f-128">描述</span><span class="sxs-lookup"><span data-stu-id="a0a6f-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a0a6f-129">GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a0a6f-129">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="a0a6f-130">定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="a0a6f-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a0a6f-131">備註</span><span class="sxs-lookup"><span data-stu-id="a0a6f-131">Remarks</span></span>

<span data-ttu-id="a0a6f-132">當您定義選取條件時，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="a0a6f-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="a0a6f-133">選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="a0a6f-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="a0a6f-134">選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="a0a6f-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="a0a6f-135">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a0a6f-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a0a6f-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0a6f-136">See Also</span></span>

[<span data-ttu-id="a0a6f-137">檢視之 CustomControl 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a0a6f-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a0a6f-138">檢視之 CustomControl 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a0a6f-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a0a6f-139">SelectionCondition 的 SelectionSetName 元素，用於 View (格式的自訂控制項) </span><span class="sxs-lookup"><span data-stu-id="a0a6f-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a0a6f-140">GroupBy (格式的 SelectionCondition 的 TypeName 元素) </span><span class="sxs-lookup"><span data-stu-id="a0a6f-140">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="a0a6f-141">GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a0a6f-141">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="a0a6f-142">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="a0a6f-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
