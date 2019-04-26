---
title: WideControl （格式） 的 EntrySelectedBy SelectionCondition 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063973"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="61642-102">WideControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="61642-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="61642-103">定義要使用此定義必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="61642-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="61642-104">選取範圍條件可指定寬的項目定義的數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="61642-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="61642-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry 項目 （格式） EntrySelectedBy 項目用於 WideEntry （格式） SelectionCondition 元素WideEntry （格式） 的 EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="61642-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="61642-106">語法</span><span class="sxs-lookup"><span data-stu-id="61642-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="61642-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="61642-107">Attributes and Elements</span></span>

<span data-ttu-id="61642-108">下列各節說明屬性、 子項目和父項目`SelectionCondition`項目。</span><span class="sxs-lookup"><span data-stu-id="61642-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="61642-109">您必須指定單一`PropertyName`或`ScriptBlock`項目。</span><span class="sxs-lookup"><span data-stu-id="61642-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="61642-110">`SelectionSetName`和`TypeName`元素是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="61642-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="61642-111">您可以指定其中一個可能是項目。</span><span class="sxs-lookup"><span data-stu-id="61642-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="61642-112">屬性</span><span class="sxs-lookup"><span data-stu-id="61642-112">Attributes</span></span>

<span data-ttu-id="61642-113">無。</span><span class="sxs-lookup"><span data-stu-id="61642-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="61642-114">子元素</span><span class="sxs-lookup"><span data-stu-id="61642-114">Child Elements</span></span>

|<span data-ttu-id="61642-115">元素</span><span class="sxs-lookup"><span data-stu-id="61642-115">Element</span></span>|<span data-ttu-id="61642-116">描述</span><span class="sxs-lookup"><span data-stu-id="61642-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="61642-117">PropertyName WideEntry （格式） 的 EntrySelectedBy 的 SelectionCondition 的項目</span><span class="sxs-lookup"><span data-stu-id="61642-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="61642-118">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="61642-118">Optional element.</span></span><br /><br /> <span data-ttu-id="61642-119">指定觸發條件的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="61642-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="61642-120">針對 WideEntry （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="61642-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="61642-121">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="61642-121">Optional element.</span></span><br /><br /> <span data-ttu-id="61642-122">指定觸發條件的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="61642-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="61642-123">針對 WideEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="61642-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="61642-124">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="61642-124">Optional element.</span></span><br /><br /> <span data-ttu-id="61642-125">指定觸發條件的.NET 型別集。</span><span class="sxs-lookup"><span data-stu-id="61642-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="61642-126">針對 WideEntry （格式） 的 EntrySelectedBy SelectionCondition TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="61642-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="61642-127">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="61642-127">Optional element.</span></span><br /><br /> <span data-ttu-id="61642-128">指定觸發條件的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="61642-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="61642-129">父項目</span><span class="sxs-lookup"><span data-stu-id="61642-129">Parent Elements</span></span>

|<span data-ttu-id="61642-130">項目</span><span class="sxs-lookup"><span data-stu-id="61642-130">Element</span></span>|<span data-ttu-id="61642-131">描述</span><span class="sxs-lookup"><span data-stu-id="61642-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="61642-132">EntrySelectedBy WideEntry （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="61642-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="61642-133">定義.NET 型別，使用此寬的項目或要使用此項目必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="61642-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="61642-134">備註</span><span class="sxs-lookup"><span data-stu-id="61642-134">Remarks</span></span>

<span data-ttu-id="61642-135">每個寬的項目必須至少一個型別名稱、 選取項目集或選擇條件的定義。</span><span class="sxs-lookup"><span data-stu-id="61642-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="61642-136">在您定義的選取範圍條件時，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="61642-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="61642-137">選取條件必須指定至少一個屬性名稱或指令碼區塊，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="61642-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="61642-138">選取條件可以指定任意數目的.NET 型別，或選取項目集，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="61642-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="61642-139">如需如何使用選擇條件的詳細資訊，請參閱[定義條件時檢視項目或項目用](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="61642-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="61642-140">寬型檢視的其他元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="61642-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="61642-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61642-141">See Also</span></span>

[<span data-ttu-id="61642-142">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="61642-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="61642-143">定義何時顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="61642-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="61642-144">EntrySelectedBy WideEntry （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="61642-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="61642-145">PropertyName WideEntry （格式） 的 EntrySelectedBy 的 SelectionCondition 的項目</span><span class="sxs-lookup"><span data-stu-id="61642-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="61642-146">針對 WideEntry （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="61642-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="61642-147">針對 WideEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="61642-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="61642-148">針對 WideEntry （格式） 的 EntrySelectedBy SelectionCondition TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="61642-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="61642-149">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="61642-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
