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
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="0b031-102">WideControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0b031-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="0b031-103">定義必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="0b031-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="0b031-104">針對寬專案定義可以指定的選取條件數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="0b031-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="0b031-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（格式）之 entryselectedby 元素（代表的 WideEntry （格式） SelectionCondition 元素）WideEntry 的之 entryselectedby （格式）</span><span class="sxs-lookup"><span data-stu-id="0b031-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0b031-106">語法</span><span class="sxs-lookup"><span data-stu-id="0b031-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0b031-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="0b031-107">Attributes and Elements</span></span>

<span data-ttu-id="0b031-108">下列各節說明屬性、子專案，以及 `SelectionCondition` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="0b031-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="0b031-109">您必須指定單一 `PropertyName` 或 `ScriptBlock` 元素。</span><span class="sxs-lookup"><span data-stu-id="0b031-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="0b031-110">`SelectionSetName` 和 `TypeName` 元素是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="0b031-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="0b031-111">您可以指定其中一個元素。</span><span class="sxs-lookup"><span data-stu-id="0b031-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0b031-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0b031-112">Attributes</span></span>

<span data-ttu-id="0b031-113">無。</span><span class="sxs-lookup"><span data-stu-id="0b031-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0b031-114">子元素</span><span class="sxs-lookup"><span data-stu-id="0b031-114">Child Elements</span></span>

|<span data-ttu-id="0b031-115">項目</span><span class="sxs-lookup"><span data-stu-id="0b031-115">Element</span></span>|<span data-ttu-id="0b031-116">說明</span><span class="sxs-lookup"><span data-stu-id="0b031-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0b031-117">WideEntry 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0b031-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="0b031-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="0b031-118">Optional element.</span></span><br /><br /> <span data-ttu-id="0b031-119">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="0b031-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="0b031-120">WideEntry 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0b031-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="0b031-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="0b031-121">Optional element.</span></span><br /><br /> <span data-ttu-id="0b031-122">指定觸發條件的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="0b031-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="0b031-123">WideEntry 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0b031-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="0b031-124">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="0b031-124">Optional element.</span></span><br /><br /> <span data-ttu-id="0b031-125">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="0b031-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="0b031-126">WideEntry 之之 entryselectedby 的 SelectionCondition 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0b031-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="0b031-127">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="0b031-127">Optional element.</span></span><br /><br /> <span data-ttu-id="0b031-128">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="0b031-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0b031-129">父元素</span><span class="sxs-lookup"><span data-stu-id="0b031-129">Parent Elements</span></span>

|<span data-ttu-id="0b031-130">項目</span><span class="sxs-lookup"><span data-stu-id="0b031-130">Element</span></span>|<span data-ttu-id="0b031-131">說明</span><span class="sxs-lookup"><span data-stu-id="0b031-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0b031-132">WideEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0b031-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="0b031-133">定義使用此寬專案的 .NET 類型，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="0b031-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0b031-134">備註</span><span class="sxs-lookup"><span data-stu-id="0b031-134">Remarks</span></span>

<span data-ttu-id="0b031-135">每個寬專案都必須定義至少一個型別名稱、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="0b031-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="0b031-136">當您定義選取條件時，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="0b031-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="0b031-137">選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="0b031-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="0b031-138">選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="0b031-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="0b031-139">如需如何使用選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="0b031-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="0b031-140">如需有關寬視圖之其他元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="0b031-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0b031-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b031-141">See Also</span></span>

[<span data-ttu-id="0b031-142">建立寬型視圖</span><span class="sxs-lookup"><span data-stu-id="0b031-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="0b031-143">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="0b031-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="0b031-144">WideEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0b031-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="0b031-145">WideEntry 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0b031-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="0b031-146">WideEntry 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0b031-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="0b031-147">WideEntry 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0b031-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="0b031-148">WideEntry 之之 entryselectedby 的 SelectionCondition 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0b031-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="0b031-149">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="0b031-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
