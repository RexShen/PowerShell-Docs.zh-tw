---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)
description: TableControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: a5a395f718d0e1a2d7f33d120ce4fd2ff787cc34
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651781"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="af075-103">TableControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="af075-103">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="af075-104">指定使用此資料表視圖專案的一組 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="af075-104">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="af075-105">可以針對專案指定的選取範圍數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="af075-105">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="af075-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) TableRowEntries 元素 (格式) TableRowEntry 專案 (格式) 之 entryselectedby 專案 (格式) SelectionSetName 專案之 entryselectedby 的 TableRowEntry (格式) </span><span class="sxs-lookup"><span data-stu-id="af075-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="af075-107">語法</span><span class="sxs-lookup"><span data-stu-id="af075-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="af075-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="af075-108">Attributes and Elements</span></span>

<span data-ttu-id="af075-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="af075-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="af075-110">屬性</span><span class="sxs-lookup"><span data-stu-id="af075-110">Attributes</span></span>

<span data-ttu-id="af075-111">無。</span><span class="sxs-lookup"><span data-stu-id="af075-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="af075-112">子元素</span><span class="sxs-lookup"><span data-stu-id="af075-112">Child Elements</span></span>

<span data-ttu-id="af075-113">無。</span><span class="sxs-lookup"><span data-stu-id="af075-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="af075-114">父項目</span><span class="sxs-lookup"><span data-stu-id="af075-114">Parent Elements</span></span>

|<span data-ttu-id="af075-115">元素</span><span class="sxs-lookup"><span data-stu-id="af075-115">Element</span></span>|<span data-ttu-id="af075-116">描述</span><span class="sxs-lookup"><span data-stu-id="af075-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="af075-117">之 entryselectedby 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="af075-117">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="af075-118">定義使用此專案的 .NET 型別，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="af075-118">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="af075-119">文字值</span><span class="sxs-lookup"><span data-stu-id="af075-119">Text Value</span></span>

<span data-ttu-id="af075-120">指定選項群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="af075-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="af075-121">備註</span><span class="sxs-lookup"><span data-stu-id="af075-121">Remarks</span></span>

<span data-ttu-id="af075-122">當您想要定義多個視圖中使用的一組物件時，通常會使用選取集。</span><span class="sxs-lookup"><span data-stu-id="af075-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="af075-123">例如，您可能會想要為相同的物件集建立資料表視圖和清單視圖。</span><span class="sxs-lookup"><span data-stu-id="af075-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="af075-124">如需定義選擇集的詳細資訊，請參閱 [定義視圖的物件集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="af075-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="af075-125">如果您指定專案的選取範圍，就不能指定型別名稱。</span><span class="sxs-lookup"><span data-stu-id="af075-125">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="af075-126">如需如何指定 .NET 類型的詳細資訊，請參閱適用于 [TableRowEntry 的之 entryselectedby 的 TypeName 元素 (格式) ](./typename-element-for-entryselectedby-for-tablecontrol-format.md)。</span><span class="sxs-lookup"><span data-stu-id="af075-126">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="af075-127">如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="af075-127">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="af075-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af075-128">See Also</span></span>

[<span data-ttu-id="af075-129">之 entryselectedby 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="af075-129">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="af075-130">定義視圖的物件集</span><span class="sxs-lookup"><span data-stu-id="af075-130">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="af075-131">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="af075-131">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="af075-132">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="af075-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
