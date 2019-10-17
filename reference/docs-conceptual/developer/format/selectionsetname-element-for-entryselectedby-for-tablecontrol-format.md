---
title: TableControl 之之 entryselectedby 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368317"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="d7c63-102">TableControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d7c63-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="d7c63-103">指定一組 .NET 類型，使用此資料表視圖的專案。</span><span class="sxs-lookup"><span data-stu-id="d7c63-103">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="d7c63-104">可以為專案指定的選擇集數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="d7c63-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="d7c63-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（格式）之 entryselectedby 元素（格式） SelectionSetName 專案TableRowEntry 的之 entryselectedby （格式）</span><span class="sxs-lookup"><span data-stu-id="d7c63-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d7c63-106">語法</span><span class="sxs-lookup"><span data-stu-id="d7c63-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d7c63-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="d7c63-107">Attributes and Elements</span></span>

<span data-ttu-id="d7c63-108">下列各節說明屬性、子項目和父元素。</span><span class="sxs-lookup"><span data-stu-id="d7c63-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d7c63-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d7c63-109">Attributes</span></span>

<span data-ttu-id="d7c63-110">無。</span><span class="sxs-lookup"><span data-stu-id="d7c63-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d7c63-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d7c63-111">Child Elements</span></span>

<span data-ttu-id="d7c63-112">無。</span><span class="sxs-lookup"><span data-stu-id="d7c63-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d7c63-113">父元素</span><span class="sxs-lookup"><span data-stu-id="d7c63-113">Parent Elements</span></span>

|<span data-ttu-id="d7c63-114">元素</span><span class="sxs-lookup"><span data-stu-id="d7c63-114">Element</span></span>|<span data-ttu-id="d7c63-115">描述</span><span class="sxs-lookup"><span data-stu-id="d7c63-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d7c63-116">之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d7c63-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="d7c63-117">定義使用此專案的 .NET 類型，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="d7c63-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d7c63-118">文字值</span><span class="sxs-lookup"><span data-stu-id="d7c63-118">Text Value</span></span>

<span data-ttu-id="d7c63-119">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="d7c63-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7c63-120">備註</span><span class="sxs-lookup"><span data-stu-id="d7c63-120">Remarks</span></span>

<span data-ttu-id="d7c63-121">當您想要定義多個視圖中使用的一組物件時，通常會使用選取範圍集。</span><span class="sxs-lookup"><span data-stu-id="d7c63-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="d7c63-122">例如，您可能會想要建立一組相同物件的資料表視圖和清單視圖。</span><span class="sxs-lookup"><span data-stu-id="d7c63-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="d7c63-123">如需定義選取集的詳細資訊，請參閱[定義視圖的物件集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="d7c63-123">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="d7c63-124">如果您指定專案的選擇集，則無法指定類型名稱。</span><span class="sxs-lookup"><span data-stu-id="d7c63-124">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="d7c63-125">如需如何指定 .NET 類型的詳細資訊，請參閱[之 entryselectedby For TableRowEntry 的 TypeName 元素（格式）](./typename-element-for-entryselectedby-for-tablecontrol-format.md)。</span><span class="sxs-lookup"><span data-stu-id="d7c63-125">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="d7c63-126">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d7c63-126">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d7c63-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7c63-127">See Also</span></span>

[<span data-ttu-id="d7c63-128">之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d7c63-128">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="d7c63-129">定義視圖的物件集合</span><span class="sxs-lookup"><span data-stu-id="d7c63-129">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="d7c63-130">建立資料表視圖</span><span class="sxs-lookup"><span data-stu-id="d7c63-130">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d7c63-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="d7c63-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)