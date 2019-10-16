---
title: CustomControl for View 的 CustomEntry 的之 entryselectedby 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368777"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="a8fc6-102">檢視之 CustomControl 的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a8fc6-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="a8fc6-103">定義使用此自訂專案的 .NET 類型，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="a8fc6-103">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="a8fc6-104">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素（format） CustomEntries 元素，適用于 CustomEntry for View 的 CustomControl for View （format） CustomEntries 元素（格式）之 entryselectedbyView 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a8fc6-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a8fc6-105">語法</span><span class="sxs-lookup"><span data-stu-id="a8fc6-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a8fc6-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="a8fc6-106">Attributes and Elements</span></span>

<span data-ttu-id="a8fc6-107">下列各節說明屬性、子專案，以及 `EntrySelectedBy` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="a8fc6-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a8fc6-108">屬性</span><span class="sxs-lookup"><span data-stu-id="a8fc6-108">Attributes</span></span>

<span data-ttu-id="a8fc6-109">無。</span><span class="sxs-lookup"><span data-stu-id="a8fc6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a8fc6-110">子元素</span><span class="sxs-lookup"><span data-stu-id="a8fc6-110">Child Elements</span></span>

|<span data-ttu-id="a8fc6-111">元素</span><span class="sxs-lookup"><span data-stu-id="a8fc6-111">Element</span></span>|<span data-ttu-id="a8fc6-112">描述</span><span class="sxs-lookup"><span data-stu-id="a8fc6-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a8fc6-113">CustomEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a8fc6-113">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="a8fc6-114">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="a8fc6-114">Optional element.</span></span><br /><br /> <span data-ttu-id="a8fc6-115">定義必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="a8fc6-115">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="a8fc6-116">CustomEntry 之之 entryselectedby 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a8fc6-116">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="a8fc6-117">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="a8fc6-117">Optional element.</span></span><br /><br /> <span data-ttu-id="a8fc6-118">指定一組使用此控制項視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="a8fc6-118">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="a8fc6-119">CustomEntry 之之 entryselectedby 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a8fc6-119">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="a8fc6-120">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="a8fc6-120">Optional element.</span></span><br /><br /> <span data-ttu-id="a8fc6-121">指定使用此控制項視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="a8fc6-121">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a8fc6-122">父元素</span><span class="sxs-lookup"><span data-stu-id="a8fc6-122">Parent Elements</span></span>

|<span data-ttu-id="a8fc6-123">元素</span><span class="sxs-lookup"><span data-stu-id="a8fc6-123">Element</span></span>|<span data-ttu-id="a8fc6-124">描述</span><span class="sxs-lookup"><span data-stu-id="a8fc6-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a8fc6-125">CustomEntries for View 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a8fc6-125">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="a8fc6-126">定義特定 .NET 物件所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="a8fc6-126">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a8fc6-127">備註</span><span class="sxs-lookup"><span data-stu-id="a8fc6-127">Remarks</span></span>

<span data-ttu-id="a8fc6-128">您必須為專案指定至少一種類型、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="a8fc6-128">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="a8fc6-129">您可以使用的子項目數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="a8fc6-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="a8fc6-130">選取條件是用來定義要使用的專案必須存在的條件，例如當物件具有特定屬性時，或特定屬性值或腳本評估為 `true` 時。</span><span class="sxs-lookup"><span data-stu-id="a8fc6-130">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="a8fc6-131">如需選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a8fc6-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a8fc6-132">如需自訂控制項視圖之元件的詳細資訊，請參閱[自訂控制項視圖](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="a8fc6-132">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a8fc6-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8fc6-133">See Also</span></span>

[<span data-ttu-id="a8fc6-134">CustomEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a8fc6-134">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="a8fc6-135">CustomEntry 之之 entryselectedby 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a8fc6-135">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a8fc6-136">CustomEntry 之之 entryselectedby 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a8fc6-136">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a8fc6-137">CustomEntries for View 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a8fc6-137">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a8fc6-138">自訂控制項視圖</span><span class="sxs-lookup"><span data-stu-id="a8fc6-138">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="a8fc6-139">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="a8fc6-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
