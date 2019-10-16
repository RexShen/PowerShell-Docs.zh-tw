---
title: WideControl 之之 entryselectedby 的 SelectionCondition 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364777"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="336d3-102">WideControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="336d3-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="336d3-103">定義必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="336d3-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="336d3-104">針對寬專案定義可以指定的選取條件數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="336d3-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="336d3-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（格式）之 entryselectedby 元素（代表的 WideEntry （格式） SelectionCondition 元素）WideEntry 的之 entryselectedby （格式）</span><span class="sxs-lookup"><span data-stu-id="336d3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="336d3-106">語法</span><span class="sxs-lookup"><span data-stu-id="336d3-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="336d3-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="336d3-107">Attributes and Elements</span></span>

<span data-ttu-id="336d3-108">下列各節說明屬性、子專案，以及 `SelectionCondition` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="336d3-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="336d3-109">您必須指定單一 `PropertyName` 或 @no__t 1 元素。</span><span class="sxs-lookup"><span data-stu-id="336d3-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="336d3-110">@No__t-0 和 @no__t 1 元素是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="336d3-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="336d3-111">您可以指定其中一個元素。</span><span class="sxs-lookup"><span data-stu-id="336d3-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="336d3-112">屬性</span><span class="sxs-lookup"><span data-stu-id="336d3-112">Attributes</span></span>

<span data-ttu-id="336d3-113">無。</span><span class="sxs-lookup"><span data-stu-id="336d3-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="336d3-114">子元素</span><span class="sxs-lookup"><span data-stu-id="336d3-114">Child Elements</span></span>

|<span data-ttu-id="336d3-115">元素</span><span class="sxs-lookup"><span data-stu-id="336d3-115">Element</span></span>|<span data-ttu-id="336d3-116">描述</span><span class="sxs-lookup"><span data-stu-id="336d3-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="336d3-117">WideEntry 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="336d3-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="336d3-118">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="336d3-118">Optional element.</span></span><br /><br /> <span data-ttu-id="336d3-119">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="336d3-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="336d3-120">WideEntry 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="336d3-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="336d3-121">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="336d3-121">Optional element.</span></span><br /><br /> <span data-ttu-id="336d3-122">指定觸發條件的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="336d3-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="336d3-123">WideEntry 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="336d3-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="336d3-124">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="336d3-124">Optional element.</span></span><br /><br /> <span data-ttu-id="336d3-125">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="336d3-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="336d3-126">WideEntry 之之 entryselectedby 的 SelectionCondition 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="336d3-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="336d3-127">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="336d3-127">Optional element.</span></span><br /><br /> <span data-ttu-id="336d3-128">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="336d3-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="336d3-129">父元素</span><span class="sxs-lookup"><span data-stu-id="336d3-129">Parent Elements</span></span>

|<span data-ttu-id="336d3-130">元素</span><span class="sxs-lookup"><span data-stu-id="336d3-130">Element</span></span>|<span data-ttu-id="336d3-131">描述</span><span class="sxs-lookup"><span data-stu-id="336d3-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="336d3-132">WideEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="336d3-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="336d3-133">定義使用此寬專案的 .NET 類型，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="336d3-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="336d3-134">備註</span><span class="sxs-lookup"><span data-stu-id="336d3-134">Remarks</span></span>

<span data-ttu-id="336d3-135">每個寬專案都必須定義至少一個型別名稱、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="336d3-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="336d3-136">當您定義選取條件時，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="336d3-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="336d3-137">選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="336d3-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="336d3-138">選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="336d3-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="336d3-139">如需如何使用選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="336d3-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="336d3-140">如需有關寬視圖之其他元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="336d3-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="336d3-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="336d3-141">See Also</span></span>

[<span data-ttu-id="336d3-142">建立寬型視圖</span><span class="sxs-lookup"><span data-stu-id="336d3-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="336d3-143">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="336d3-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="336d3-144">WideEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="336d3-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="336d3-145">WideEntry 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="336d3-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="336d3-146">WideEntry 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="336d3-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="336d3-147">WideEntry 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="336d3-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="336d3-148">WideEntry 之之 entryselectedby 的 SelectionCondition 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="336d3-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="336d3-149">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="336d3-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
