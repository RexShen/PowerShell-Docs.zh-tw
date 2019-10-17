---
title: GroupBy 之 CustomEntry 的之 entryselectedby 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363857"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="eb47b-102">GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="eb47b-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="eb47b-103">定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="eb47b-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="eb47b-104">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="eb47b-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="eb47b-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（format） CustomEntries 專案的 groupby （format） CustomControl 元素，適用于的 CustomControl for GroupBy （format） CustomEntry 元素適用于 GroupBy 之 CustomEntry 的 GroupBy （Format）之 entryselectedby 元素 CustomControl （格式）</span><span class="sxs-lookup"><span data-stu-id="eb47b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="eb47b-106">語法</span><span class="sxs-lookup"><span data-stu-id="eb47b-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="eb47b-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="eb47b-107">Attributes and Elements</span></span>

<span data-ttu-id="eb47b-108">下列各節描述 `EntrySelectedBy` 元素的屬性、子專案和父元素。</span><span class="sxs-lookup"><span data-stu-id="eb47b-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="eb47b-109">您必須為定義指定至少一個類型、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="eb47b-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="eb47b-110">您可以使用的子項目數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="eb47b-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="eb47b-111">屬性</span><span class="sxs-lookup"><span data-stu-id="eb47b-111">Attributes</span></span>

<span data-ttu-id="eb47b-112">無。</span><span class="sxs-lookup"><span data-stu-id="eb47b-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="eb47b-113">子元素</span><span class="sxs-lookup"><span data-stu-id="eb47b-113">Child Elements</span></span>

|<span data-ttu-id="eb47b-114">元素</span><span class="sxs-lookup"><span data-stu-id="eb47b-114">Element</span></span>|<span data-ttu-id="eb47b-115">描述</span><span class="sxs-lookup"><span data-stu-id="eb47b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eb47b-116">GroupBy 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="eb47b-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="eb47b-117">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="eb47b-117">Optional element.</span></span><br /><br /> <span data-ttu-id="eb47b-118">定義必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="eb47b-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="eb47b-119">GroupBy 之之 entryselectedby 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="eb47b-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="eb47b-120">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="eb47b-120">Optional element.</span></span><br /><br /> <span data-ttu-id="eb47b-121">指定一組使用此控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="eb47b-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="eb47b-122">GroupBy 之之 entryselectedby 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="eb47b-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="eb47b-123">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="eb47b-123">Optional element.</span></span><br /><br /> <span data-ttu-id="eb47b-124">指定使用此控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="eb47b-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="eb47b-125">父元素</span><span class="sxs-lookup"><span data-stu-id="eb47b-125">Parent Elements</span></span>

|<span data-ttu-id="eb47b-126">元素</span><span class="sxs-lookup"><span data-stu-id="eb47b-126">Element</span></span>|<span data-ttu-id="eb47b-127">描述</span><span class="sxs-lookup"><span data-stu-id="eb47b-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eb47b-128">GroupBy 之 CustomControl 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="eb47b-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="eb47b-129">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="eb47b-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="eb47b-130">備註</span><span class="sxs-lookup"><span data-stu-id="eb47b-130">Remarks</span></span>

<span data-ttu-id="eb47b-131">選取條件是用來定義要使用的定義必須存在的條件，例如當物件具有特定屬性時，或特定屬性值或腳本評估為 `true` 時。</span><span class="sxs-lookup"><span data-stu-id="eb47b-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="eb47b-132">如需選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="eb47b-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eb47b-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb47b-133">See Also</span></span>

[<span data-ttu-id="eb47b-134">GroupBy 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="eb47b-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="eb47b-135">GroupBy 之之 entryselectedby 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="eb47b-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="eb47b-136">GroupBy 之之 entryselectedby 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="eb47b-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="eb47b-137">View 之控制項的 CustomEntries 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="eb47b-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="eb47b-138">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="eb47b-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)