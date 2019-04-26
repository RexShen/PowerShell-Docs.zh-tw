---
title: CustomControl 檢視 （格式） 的 CustomEntry EntrySelectedBy 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066272"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="02532-102">檢視之 CustomControl 的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="02532-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="02532-103">定義.NET 型別，使用此自訂的項目或要使用此項目必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="02532-103">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="02532-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目 （格式） CustomEntries 項目 CustomControl 檢視 （格式） 的檢視 （格式） EntrySelectedBy CustomEntries CustomEntry 元素CustomEntry 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="02532-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="02532-105">語法</span><span class="sxs-lookup"><span data-stu-id="02532-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="02532-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="02532-106">Attributes and Elements</span></span>

<span data-ttu-id="02532-107">下列各節說明屬性、 子項目和父項目`EntrySelectedBy`項目。</span><span class="sxs-lookup"><span data-stu-id="02532-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="02532-108">屬性</span><span class="sxs-lookup"><span data-stu-id="02532-108">Attributes</span></span>

<span data-ttu-id="02532-109">無。</span><span class="sxs-lookup"><span data-stu-id="02532-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="02532-110">子元素</span><span class="sxs-lookup"><span data-stu-id="02532-110">Child Elements</span></span>

|<span data-ttu-id="02532-111">元素</span><span class="sxs-lookup"><span data-stu-id="02532-111">Element</span></span>|<span data-ttu-id="02532-112">描述</span><span class="sxs-lookup"><span data-stu-id="02532-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="02532-113">CustomEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="02532-113">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="02532-114">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="02532-114">Optional element.</span></span><br /><br /> <span data-ttu-id="02532-115">定義要使用此定義必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="02532-115">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="02532-116">CustomEntry （格式） 的 EntrySelectedBy SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="02532-116">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="02532-117">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="02532-117">Optional element.</span></span><br /><br /> <span data-ttu-id="02532-118">指定一組使用的控制項檢視此定義的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="02532-118">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="02532-119">CustomEntry （格式） 的 EntrySelectedBy TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="02532-119">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="02532-120">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="02532-120">Optional element.</span></span><br /><br /> <span data-ttu-id="02532-121">指定使用的控制項檢視此定義的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="02532-121">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="02532-122">父項目</span><span class="sxs-lookup"><span data-stu-id="02532-122">Parent Elements</span></span>

|<span data-ttu-id="02532-123">項目</span><span class="sxs-lookup"><span data-stu-id="02532-123">Element</span></span>|<span data-ttu-id="02532-124">描述</span><span class="sxs-lookup"><span data-stu-id="02532-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="02532-125">CustomEntry CustomEntries 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="02532-125">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="02532-126">定義特定的.NET 物件所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="02532-126">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="02532-127">備註</span><span class="sxs-lookup"><span data-stu-id="02532-127">Remarks</span></span>

<span data-ttu-id="02532-128">您必須指定至少一個型別、 選取項目集或選擇條件的項目。</span><span class="sxs-lookup"><span data-stu-id="02532-128">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="02532-129">沒有任何子項目的，您可以使用數字的最大限制。</span><span class="sxs-lookup"><span data-stu-id="02532-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="02532-130">選擇條件用來定義的條件必須存在於要使用的項目，例如當物件只有特定的屬性時，或特定的屬性值，或指令碼會評估`true`。</span><span class="sxs-lookup"><span data-stu-id="02532-130">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="02532-131">如需有關選擇條件的詳細資訊，請參閱[定義條件時檢視項目或項目用](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="02532-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="02532-132">如需詳細的自訂控制項的檢視元件的相關資訊，請參閱[自訂的控制項檢視](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="02532-132">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="02532-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02532-133">See Also</span></span>

[<span data-ttu-id="02532-134">CustomEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="02532-134">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="02532-135">CustomEntry （格式） 的 EntrySelectedBy SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="02532-135">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="02532-136">CustomEntry （格式） 的 EntrySelectedBy TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="02532-136">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="02532-137">CustomEntry CustomEntries 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="02532-137">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="02532-138">自訂的控制項檢視</span><span class="sxs-lookup"><span data-stu-id="02532-138">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="02532-139">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="02532-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
