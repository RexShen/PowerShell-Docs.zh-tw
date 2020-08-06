---
title: 之 entryselectedby 之控制項的 SelectionCondition 元素，用於設定 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 748aa1aa0ba603a44334d9401e9e2c0e68f14e03
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783410"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="5944b-102">設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5944b-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="5944b-103">定義必須存在的條件，才能使用通用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="5944b-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="5944b-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="5944b-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="5944b-105">Configuration 專案 (格式) 控制設定的控制項元素 (格式設定的控制項) 控制項專案 (格式) 設定 (格式的控制項的 CustomControl 的 CustomEntries 元素) 設定 (格式) CustomControl 元素適用于之 entryselectedby for CustomEntry for SelectionCondition for configuration (之 entryselectedby 專案的 CustomEntry 元素) 設定的專案</span><span class="sxs-lookup"><span data-stu-id="5944b-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5944b-106">語法</span><span class="sxs-lookup"><span data-stu-id="5944b-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5944b-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5944b-107">Attributes and Elements</span></span>

<span data-ttu-id="5944b-108">下列各節說明屬性、子專案和元素的父元素 `SelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="5944b-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5944b-109">屬性</span><span class="sxs-lookup"><span data-stu-id="5944b-109">Attributes</span></span>

<span data-ttu-id="5944b-110">無。</span><span class="sxs-lookup"><span data-stu-id="5944b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5944b-111">子元素</span><span class="sxs-lookup"><span data-stu-id="5944b-111">Child Elements</span></span>

|<span data-ttu-id="5944b-112">元素</span><span class="sxs-lookup"><span data-stu-id="5944b-112">Element</span></span>|<span data-ttu-id="5944b-113">描述</span><span class="sxs-lookup"><span data-stu-id="5944b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5944b-114">設定之控制項的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5944b-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="5944b-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="5944b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="5944b-116">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="5944b-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="5944b-117">設定之控制項的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5944b-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="5944b-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="5944b-118">Optional element.</span></span><br /><br /> <span data-ttu-id="5944b-119">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="5944b-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="5944b-120">設定之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5944b-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="5944b-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="5944b-121">Optional element.</span></span><br /><br /> <span data-ttu-id="5944b-122">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="5944b-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="5944b-123">設定之控制項的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5944b-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="5944b-124">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="5944b-124">Optional element.</span></span><br /><br /> <span data-ttu-id="5944b-125">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="5944b-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5944b-126">父項目</span><span class="sxs-lookup"><span data-stu-id="5944b-126">Parent Elements</span></span>

|<span data-ttu-id="5944b-127">元素</span><span class="sxs-lookup"><span data-stu-id="5944b-127">Element</span></span>|<span data-ttu-id="5944b-128">描述</span><span class="sxs-lookup"><span data-stu-id="5944b-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5944b-129">設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5944b-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="5944b-130">定義使用此通用控制項定義之專案的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="5944b-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5944b-131">備註</span><span class="sxs-lookup"><span data-stu-id="5944b-131">Remarks</span></span>

<span data-ttu-id="5944b-132">定義選取條件時，必須遵循下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="5944b-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="5944b-133">選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="5944b-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="5944b-134">選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="5944b-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="5944b-135">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5944b-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5944b-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5944b-136">See Also</span></span>

[<span data-ttu-id="5944b-137">設定之控制項的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5944b-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="5944b-138">設定之控制項的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5944b-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="5944b-139">設定之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5944b-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="5944b-140">設定之控制項的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5944b-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="5944b-141">設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5944b-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="5944b-142">撰寫 Windows PowerShell 格式化和類型檔案</span><span class="sxs-lookup"><span data-stu-id="5944b-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
