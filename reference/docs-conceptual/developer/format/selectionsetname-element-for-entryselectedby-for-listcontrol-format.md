---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)
description: ListControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: 413a77f7ba06fe952e574061e58d0b5d80c5b3c4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651827"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="d8d55-103">ListControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d8d55-103">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="d8d55-104">指定清單專案的一組 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="d8d55-104">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="d8d55-105">可以針對專案指定的選取範圍數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="d8d55-105">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="d8d55-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 元素 (格式) ListEntries 元素 (格式) ListEntry 專案 (格式) 之 entryselectedby 專案 (格式) ListEntry 專案 SelectionSetName 的之 entryselectedby (格式) </span><span class="sxs-lookup"><span data-stu-id="d8d55-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d8d55-107">語法</span><span class="sxs-lookup"><span data-stu-id="d8d55-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d8d55-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d8d55-108">Attributes and Elements</span></span>

<span data-ttu-id="d8d55-109">下列各節描述專案的屬性、子項目和父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="d8d55-109">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d8d55-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d8d55-110">Attributes</span></span>

<span data-ttu-id="d8d55-111">無。</span><span class="sxs-lookup"><span data-stu-id="d8d55-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d8d55-112">子元素</span><span class="sxs-lookup"><span data-stu-id="d8d55-112">Child Elements</span></span>

<span data-ttu-id="d8d55-113">無。</span><span class="sxs-lookup"><span data-stu-id="d8d55-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d8d55-114">父項目</span><span class="sxs-lookup"><span data-stu-id="d8d55-114">Parent Elements</span></span>

|<span data-ttu-id="d8d55-115">元素</span><span class="sxs-lookup"><span data-stu-id="d8d55-115">Element</span></span>|<span data-ttu-id="d8d55-116">描述</span><span class="sxs-lookup"><span data-stu-id="d8d55-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d8d55-117">ListEntry (格式的之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="d8d55-117">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="d8d55-118">定義使用此清單專案的 .NET 型別，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="d8d55-118">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d8d55-119">文字值</span><span class="sxs-lookup"><span data-stu-id="d8d55-119">Text Value</span></span>

<span data-ttu-id="d8d55-120">指定選項群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="d8d55-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="d8d55-121">備註</span><span class="sxs-lookup"><span data-stu-id="d8d55-121">Remarks</span></span>

<span data-ttu-id="d8d55-122">每個清單專案都必須定義至少一個類型名稱、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="d8d55-122">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="d8d55-123">當您想要定義多個視圖中使用的一組物件時，通常會使用選取集。</span><span class="sxs-lookup"><span data-stu-id="d8d55-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="d8d55-124">例如，您可能會想要為相同的物件集建立資料表視圖和清單視圖。</span><span class="sxs-lookup"><span data-stu-id="d8d55-124">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="d8d55-125">如需定義選擇集的詳細資訊，請參閱 [定義視圖的物件集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="d8d55-125">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="d8d55-126">如需清單視圖元件的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d8d55-126">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d8d55-127">範例</span><span class="sxs-lookup"><span data-stu-id="d8d55-127">Example</span></span>

<span data-ttu-id="d8d55-128">下列範例示範如何為清單視圖的專案指定選取集。</span><span class="sxs-lookup"><span data-stu-id="d8d55-128">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="d8d55-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8d55-129">See Also</span></span>

[<span data-ttu-id="d8d55-130">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="d8d55-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d8d55-131">ListEntry (格式的之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="d8d55-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="d8d55-132">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="d8d55-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
