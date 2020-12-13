---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)
description: WideControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)
ms.openlocfilehash: 8c51ca72edc6ad174dc289c61a8987e8f9495d19
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655118"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="ed9ef-103">WideControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ed9ef-103">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="ed9ef-104">定義必須存在的條件，才能使用這個定義。</span><span class="sxs-lookup"><span data-stu-id="ed9ef-104">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="ed9ef-105">可以針對寬專案定義指定的選取條件數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="ed9ef-105">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="ed9ef-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) WideControl 元素 (格式) WideEntries 元素 (格式) WideEntry 專案 (格式) 之 entryselectedby 專案 (格式) WideEntry 專案 SelectionCondition 的之 entryselectedby (格式) </span><span class="sxs-lookup"><span data-stu-id="ed9ef-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ed9ef-107">語法</span><span class="sxs-lookup"><span data-stu-id="ed9ef-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ed9ef-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ed9ef-108">Attributes and Elements</span></span>

<span data-ttu-id="ed9ef-109">下列各節說明屬性、子專案和元素的父元素 `SelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="ed9ef-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="ed9ef-110">您必須指定單一 `PropertyName` 或 `ScriptBlock` 元素。</span><span class="sxs-lookup"><span data-stu-id="ed9ef-110">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="ed9ef-111">`SelectionSetName`和 `TypeName` 元素是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="ed9ef-111">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="ed9ef-112">您可以指定其中一個元素。</span><span class="sxs-lookup"><span data-stu-id="ed9ef-112">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ed9ef-113">屬性</span><span class="sxs-lookup"><span data-stu-id="ed9ef-113">Attributes</span></span>

<span data-ttu-id="ed9ef-114">無。</span><span class="sxs-lookup"><span data-stu-id="ed9ef-114">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ed9ef-115">子元素</span><span class="sxs-lookup"><span data-stu-id="ed9ef-115">Child Elements</span></span>

|<span data-ttu-id="ed9ef-116">元素</span><span class="sxs-lookup"><span data-stu-id="ed9ef-116">Element</span></span>|<span data-ttu-id="ed9ef-117">描述</span><span class="sxs-lookup"><span data-stu-id="ed9ef-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ed9ef-118">WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ed9ef-118">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="ed9ef-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="ed9ef-119">Optional element.</span></span><br /><br /> <span data-ttu-id="ed9ef-120">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="ed9ef-120">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="ed9ef-121">適用于 WideEntry (格式之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="ed9ef-121">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="ed9ef-122">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="ed9ef-122">Optional element.</span></span><br /><br /> <span data-ttu-id="ed9ef-123">指定觸發條件的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="ed9ef-123">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="ed9ef-124">WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ed9ef-124">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="ed9ef-125">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="ed9ef-125">Optional element.</span></span><br /><br /> <span data-ttu-id="ed9ef-126">指定一組觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="ed9ef-126">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="ed9ef-127">WideEntry (格式之之 entryselectedby 的 SelectionCondition 的 TypeName 元素) </span><span class="sxs-lookup"><span data-stu-id="ed9ef-127">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="ed9ef-128">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="ed9ef-128">Optional element.</span></span><br /><br /> <span data-ttu-id="ed9ef-129">指定觸發條件的 .NET 型別。</span><span class="sxs-lookup"><span data-stu-id="ed9ef-129">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ed9ef-130">父項目</span><span class="sxs-lookup"><span data-stu-id="ed9ef-130">Parent Elements</span></span>

|<span data-ttu-id="ed9ef-131">元素</span><span class="sxs-lookup"><span data-stu-id="ed9ef-131">Element</span></span>|<span data-ttu-id="ed9ef-132">描述</span><span class="sxs-lookup"><span data-stu-id="ed9ef-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ed9ef-133">WideEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ed9ef-133">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="ed9ef-134">定義使用此寬專案的 .NET 型別，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="ed9ef-134">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ed9ef-135">備註</span><span class="sxs-lookup"><span data-stu-id="ed9ef-135">Remarks</span></span>

<span data-ttu-id="ed9ef-136">每個寬專案都必須定義至少一個類型名稱、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="ed9ef-136">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="ed9ef-137">當您定義選取條件時，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="ed9ef-137">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="ed9ef-138">選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="ed9ef-138">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="ed9ef-139">選取條件可以指定任意數目的 .NET 類型或選取集，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="ed9ef-139">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="ed9ef-140">如需如何使用選取條件的詳細資訊，請參閱 [定義使用視圖專案或專案的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="ed9ef-140">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="ed9ef-141">如需更多有關廣泛視圖的元件的詳細資訊，請參閱 [建立廣泛的觀點](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="ed9ef-141">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ed9ef-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed9ef-142">See Also</span></span>

[<span data-ttu-id="ed9ef-143">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="ed9ef-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ed9ef-144">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="ed9ef-144">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ed9ef-145">WideEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ed9ef-145">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="ed9ef-146">WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ed9ef-146">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="ed9ef-147">適用于 WideEntry (格式之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="ed9ef-147">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="ed9ef-148">WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ed9ef-148">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="ed9ef-149">WideEntry (格式之之 entryselectedby 的 SelectionCondition 的 TypeName 元素) </span><span class="sxs-lookup"><span data-stu-id="ed9ef-149">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="ed9ef-150">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="ed9ef-150">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
