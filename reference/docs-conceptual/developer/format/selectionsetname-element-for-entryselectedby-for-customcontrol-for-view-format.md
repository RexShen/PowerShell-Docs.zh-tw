---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之 CustomControl 的 EntrySelectedBy 的 SelectionSetName 元素 (格式)
description: 檢視之 CustomControl 的 EntrySelectedBy 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: a158c5476fb3a168a146ce67565c0ed6f7859519
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651921"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="4bab1-103">檢視之 CustomControl 的 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4bab1-103">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="4bab1-104">指定清單專案的一組 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="4bab1-104">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="4bab1-105">可以針對專案指定的選取範圍數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="4bab1-105">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="4bab1-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 專案 (格式) CustomEntries 專案 (格式) 專案 (格式) CustomEntry 專案 (格式) CustomEntries 專案之 entryselectedby for CustomEntry 的 SelectionSetName (格式) </span><span class="sxs-lookup"><span data-stu-id="4bab1-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4bab1-107">語法</span><span class="sxs-lookup"><span data-stu-id="4bab1-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4bab1-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4bab1-108">Attributes and Elements</span></span>

<span data-ttu-id="4bab1-109">下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="4bab1-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4bab1-110">屬性</span><span class="sxs-lookup"><span data-stu-id="4bab1-110">Attributes</span></span>

<span data-ttu-id="4bab1-111">無。</span><span class="sxs-lookup"><span data-stu-id="4bab1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4bab1-112">子元素</span><span class="sxs-lookup"><span data-stu-id="4bab1-112">Child Elements</span></span>

<span data-ttu-id="4bab1-113">無。</span><span class="sxs-lookup"><span data-stu-id="4bab1-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4bab1-114">父項目</span><span class="sxs-lookup"><span data-stu-id="4bab1-114">Parent Elements</span></span>

|<span data-ttu-id="4bab1-115">元素</span><span class="sxs-lookup"><span data-stu-id="4bab1-115">Element</span></span>|<span data-ttu-id="4bab1-116">描述</span><span class="sxs-lookup"><span data-stu-id="4bab1-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4bab1-117">適用于 CustomEntry 的之 entryselectedby 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="4bab1-117">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="4bab1-118">定義使用此自訂專案的 .NET 型別，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="4bab1-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4bab1-119">文字值</span><span class="sxs-lookup"><span data-stu-id="4bab1-119">Text Value</span></span>

<span data-ttu-id="4bab1-120">指定選項群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="4bab1-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="4bab1-121">備註</span><span class="sxs-lookup"><span data-stu-id="4bab1-121">Remarks</span></span>

<span data-ttu-id="4bab1-122">每個自訂控制項專案都必須定義至少一個類型名稱、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="4bab1-122">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="4bab1-123">當您想要定義多個視圖中使用的一組物件時，通常會使用選取集。</span><span class="sxs-lookup"><span data-stu-id="4bab1-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="4bab1-124">例如，您可能會想要為相同的物件集建立資料表視圖和清單視圖。</span><span class="sxs-lookup"><span data-stu-id="4bab1-124">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="4bab1-125">如需定義選取範圍的詳細資訊，請參閱 [定義選取集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="4bab1-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="4bab1-126">如需自訂控制項視圖元件的詳細資訊，請參閱 [建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="4bab1-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4bab1-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bab1-127">See Also</span></span>

[<span data-ttu-id="4bab1-128">適用于 CustomEntry 的之 entryselectedby 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="4bab1-128">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4bab1-129">自訂控制項視圖</span><span class="sxs-lookup"><span data-stu-id="4bab1-129">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="4bab1-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="4bab1-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
