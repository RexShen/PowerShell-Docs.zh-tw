---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之 CustomControl 的 CustomEntry 的 EntrySelectedBy 元素 (格式)
description: 檢視之 CustomControl 的 CustomEntry 的 EntrySelectedBy 元素 (格式)
ms.openlocfilehash: 4821f22560f35034f90d018e5a109004f331441f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655350"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="f6460-103">檢視之 CustomControl 的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="f6460-103">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="f6460-104">定義使用此自訂專案的 .NET 型別，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="f6460-104">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="f6460-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 專案 (格式) CustomEntries 專案 (格式) 專案 (格式) CustomEntry 專案 (格式) CustomEntries 專案格式之 entryselectedby 元素</span><span class="sxs-lookup"><span data-stu-id="f6460-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f6460-106">語法</span><span class="sxs-lookup"><span data-stu-id="f6460-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f6460-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f6460-107">Attributes and Elements</span></span>

<span data-ttu-id="f6460-108">下列各節說明屬性、子專案和元素的父元素 `EntrySelectedBy` 。</span><span class="sxs-lookup"><span data-stu-id="f6460-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f6460-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f6460-109">Attributes</span></span>

<span data-ttu-id="f6460-110">無。</span><span class="sxs-lookup"><span data-stu-id="f6460-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f6460-111">子元素</span><span class="sxs-lookup"><span data-stu-id="f6460-111">Child Elements</span></span>

|<span data-ttu-id="f6460-112">元素</span><span class="sxs-lookup"><span data-stu-id="f6460-112">Element</span></span>|<span data-ttu-id="f6460-113">描述</span><span class="sxs-lookup"><span data-stu-id="f6460-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f6460-114">適用于之 entryselectedby 的 CustomEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="f6460-114">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="f6460-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f6460-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f6460-116">定義必須存在的條件，才能使用這個定義。</span><span class="sxs-lookup"><span data-stu-id="f6460-116">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="f6460-117">適用于之 entryselectedby 的 CustomEntry (格式的 SelectionSetName 元素) </span><span class="sxs-lookup"><span data-stu-id="f6460-117">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="f6460-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f6460-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f6460-119">指定一組使用此控制項的定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="f6460-119">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="f6460-120">適用于 CustomEntry 的之 entryselectedby 的 TypeName 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="f6460-120">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="f6460-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f6460-121">Optional element.</span></span><br /><br /> <span data-ttu-id="f6460-122">指定使用此控制項視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="f6460-122">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f6460-123">父項目</span><span class="sxs-lookup"><span data-stu-id="f6460-123">Parent Elements</span></span>

|<span data-ttu-id="f6460-124">元素</span><span class="sxs-lookup"><span data-stu-id="f6460-124">Element</span></span>|<span data-ttu-id="f6460-125">描述</span><span class="sxs-lookup"><span data-stu-id="f6460-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f6460-126">適用于 CustomEntries 的 CustomEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="f6460-126">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="f6460-127">定義特定 .NET 物件所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="f6460-127">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f6460-128">備註</span><span class="sxs-lookup"><span data-stu-id="f6460-128">Remarks</span></span>

<span data-ttu-id="f6460-129">您必須為專案指定至少一個類型、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="f6460-129">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="f6460-130">您可以使用的子項目數目沒有最大限制。</span><span class="sxs-lookup"><span data-stu-id="f6460-130">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="f6460-131">選取條件是用來定義必須存在的條件，才能使用專案，例如當物件有特定屬性，或當特定屬性值或腳本評估為時 `true` 。</span><span class="sxs-lookup"><span data-stu-id="f6460-131">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="f6460-132">如需選取條件的詳細資訊，請參閱 [定義使用視圖專案或專案的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f6460-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f6460-133">如需自訂控制項視圖元件的詳細資訊，請參閱 [自訂控制項視圖](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="f6460-133">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f6460-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6460-134">See Also</span></span>

[<span data-ttu-id="f6460-135">適用于之 entryselectedby 的 CustomEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="f6460-135">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="f6460-136">適用于之 entryselectedby 的 CustomEntry (格式的 SelectionSetName 元素) </span><span class="sxs-lookup"><span data-stu-id="f6460-136">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f6460-137">適用于 CustomEntry 的之 entryselectedby 的 TypeName 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="f6460-137">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f6460-138">適用于 CustomEntries 的 CustomEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="f6460-138">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f6460-139">自訂控制項視圖</span><span class="sxs-lookup"><span data-stu-id="f6460-139">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="f6460-140">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="f6460-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
