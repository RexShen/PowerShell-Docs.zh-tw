---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)
description: 設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)
ms.openlocfilehash: ce00cdf868a3075875043aeb59f2cb8a17d049a9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645773"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="4afbb-103">設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4afbb-103">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="4afbb-104">定義必須存在才能使用通用控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="4afbb-104">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="4afbb-105">當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="4afbb-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="4afbb-106">Configuration 專案 (格式) 控制項的設定 (格式) 控制項的設定 (格式) CustomControl 控制項的設定 (格式) 控制項的設定 (格式) CustomControl 專案 (格式) 之 entryselectedby 專案 (格式) CustomEntry 專案 SelectionCondition for 之 entryselectedby for CustomEntry for for for configuration (格式設定) </span><span class="sxs-lookup"><span data-stu-id="4afbb-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4afbb-107">語法</span><span class="sxs-lookup"><span data-stu-id="4afbb-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4afbb-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4afbb-108">Attributes and Elements</span></span>

<span data-ttu-id="4afbb-109">下列各節說明屬性、子專案和元素的父元素 `SelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="4afbb-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4afbb-110">屬性</span><span class="sxs-lookup"><span data-stu-id="4afbb-110">Attributes</span></span>

<span data-ttu-id="4afbb-111">無。</span><span class="sxs-lookup"><span data-stu-id="4afbb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4afbb-112">子元素</span><span class="sxs-lookup"><span data-stu-id="4afbb-112">Child Elements</span></span>

|<span data-ttu-id="4afbb-113">元素</span><span class="sxs-lookup"><span data-stu-id="4afbb-113">Element</span></span>|<span data-ttu-id="4afbb-114">描述</span><span class="sxs-lookup"><span data-stu-id="4afbb-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4afbb-115">設定之控制項的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4afbb-115">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="4afbb-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="4afbb-116">Optional element.</span></span><br /><br /> <span data-ttu-id="4afbb-117">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="4afbb-117">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="4afbb-118">設定之控制項的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4afbb-118">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="4afbb-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="4afbb-119">Optional element.</span></span><br /><br /> <span data-ttu-id="4afbb-120">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="4afbb-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="4afbb-121">設定之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4afbb-121">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="4afbb-122">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="4afbb-122">Optional element.</span></span><br /><br /> <span data-ttu-id="4afbb-123">指定一組觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="4afbb-123">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="4afbb-124">設定之控制項的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4afbb-124">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="4afbb-125">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="4afbb-125">Optional element.</span></span><br /><br /> <span data-ttu-id="4afbb-126">指定觸發條件的 .NET 型別。</span><span class="sxs-lookup"><span data-stu-id="4afbb-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4afbb-127">父項目</span><span class="sxs-lookup"><span data-stu-id="4afbb-127">Parent Elements</span></span>

|<span data-ttu-id="4afbb-128">元素</span><span class="sxs-lookup"><span data-stu-id="4afbb-128">Element</span></span>|<span data-ttu-id="4afbb-129">描述</span><span class="sxs-lookup"><span data-stu-id="4afbb-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4afbb-130">設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4afbb-130">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="4afbb-131">定義使用此通用控制項定義專案的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="4afbb-131">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4afbb-132">備註</span><span class="sxs-lookup"><span data-stu-id="4afbb-132">Remarks</span></span>

<span data-ttu-id="4afbb-133">定義選取條件時，必須遵循下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="4afbb-133">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="4afbb-134">選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="4afbb-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="4afbb-135">選取條件可以指定任意數目的 .NET 類型或選取集，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="4afbb-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="4afbb-136">如需如何使用選取條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="4afbb-136">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4afbb-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4afbb-137">See Also</span></span>

[<span data-ttu-id="4afbb-138">設定之控制項的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4afbb-138">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="4afbb-139">設定之控制項的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4afbb-139">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="4afbb-140">設定之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4afbb-140">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="4afbb-141">設定之控制項的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4afbb-141">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="4afbb-142">設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4afbb-142">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="4afbb-143">寫入 Windows PowerShell 格式和類型檔案</span><span class="sxs-lookup"><span data-stu-id="4afbb-143">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
