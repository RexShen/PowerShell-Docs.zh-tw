---
title: GroupBy （格式） 的 CustomEntry EntrySelectedBy 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066221"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="43bbd-102">GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="43bbd-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="43bbd-103">定義使用此控制項定義或必須存在於要使用此定義條件的.NET 類型。</span><span class="sxs-lookup"><span data-stu-id="43bbd-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="43bbd-104">定義新的群組物件的顯示方式時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="43bbd-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="43bbd-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素CustomControl CustomEntry 的 GroupBy （格式） 的 GroupBy （格式） EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="43bbd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="43bbd-106">語法</span><span class="sxs-lookup"><span data-stu-id="43bbd-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="43bbd-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="43bbd-107">Attributes and Elements</span></span>

<span data-ttu-id="43bbd-108">下列各節說明屬性、 子項目和父項目`EntrySelectedBy`項目。</span><span class="sxs-lookup"><span data-stu-id="43bbd-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="43bbd-109">您必須指定至少一個型別、 選取項目集或選擇條件的定義。</span><span class="sxs-lookup"><span data-stu-id="43bbd-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="43bbd-110">沒有任何子項目的，您可以使用數字的最大限制。</span><span class="sxs-lookup"><span data-stu-id="43bbd-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="43bbd-111">屬性</span><span class="sxs-lookup"><span data-stu-id="43bbd-111">Attributes</span></span>

<span data-ttu-id="43bbd-112">無。</span><span class="sxs-lookup"><span data-stu-id="43bbd-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="43bbd-113">子元素</span><span class="sxs-lookup"><span data-stu-id="43bbd-113">Child Elements</span></span>

|<span data-ttu-id="43bbd-114">元素</span><span class="sxs-lookup"><span data-stu-id="43bbd-114">Element</span></span>|<span data-ttu-id="43bbd-115">描述</span><span class="sxs-lookup"><span data-stu-id="43bbd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="43bbd-116">GroupBy （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="43bbd-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="43bbd-117">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="43bbd-117">Optional element.</span></span><br /><br /> <span data-ttu-id="43bbd-118">定義要使用此定義必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="43bbd-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="43bbd-119">GroupBy （格式） 的 EntrySelectedBy SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="43bbd-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="43bbd-120">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="43bbd-120">Optional element.</span></span><br /><br /> <span data-ttu-id="43bbd-121">指定一組使用這個控制項定義的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="43bbd-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="43bbd-122">GroupBy （格式） 的 EntrySelectedBy TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="43bbd-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="43bbd-123">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="43bbd-123">Optional element.</span></span><br /><br /> <span data-ttu-id="43bbd-124">指定使用這個控制項定義的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="43bbd-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="43bbd-125">父項目</span><span class="sxs-lookup"><span data-stu-id="43bbd-125">Parent Elements</span></span>

|<span data-ttu-id="43bbd-126">項目</span><span class="sxs-lookup"><span data-stu-id="43bbd-126">Element</span></span>|<span data-ttu-id="43bbd-127">描述</span><span class="sxs-lookup"><span data-stu-id="43bbd-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="43bbd-128">GroupBy （格式） 的 CustomControl CustomEntry 項目</span><span class="sxs-lookup"><span data-stu-id="43bbd-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="43bbd-129">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="43bbd-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="43bbd-130">備註</span><span class="sxs-lookup"><span data-stu-id="43bbd-130">Remarks</span></span>

<span data-ttu-id="43bbd-131">選擇條件用來定義的條件必須存在於使用定義，例如當物件只有特定的屬性時，或特定的屬性值，或指令碼會評估`true`。</span><span class="sxs-lookup"><span data-stu-id="43bbd-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="43bbd-132">如需有關選擇條件的詳細資訊，請參閱[定義條件時檢視項目或項目用](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="43bbd-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="43bbd-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43bbd-133">See Also</span></span>

[<span data-ttu-id="43bbd-134">GroupBy （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="43bbd-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="43bbd-135">GroupBy （格式） 的 EntrySelectedBy SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="43bbd-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="43bbd-136">GroupBy （格式） 的 EntrySelectedBy TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="43bbd-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="43bbd-137">用於檢視 （格式） 的控制項 CustomEntries CustomEntry 項目</span><span class="sxs-lookup"><span data-stu-id="43bbd-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="43bbd-138">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="43bbd-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
