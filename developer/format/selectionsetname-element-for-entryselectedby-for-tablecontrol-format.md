---
title: TableControl （格式） 的 EntrySelectedBy SelectionSetName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856094"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="0d038-102">TableControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0d038-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="0d038-103">指定一組.NET 型別使用 [資料表] 檢視的此項目。</span><span class="sxs-lookup"><span data-stu-id="0d038-103">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="0d038-104">可供指定的項目選取項目集的數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="0d038-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="0d038-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 （格式） TableRowEntry 項目 （格式） EntrySelectedBy 項目 （格式） SelectionSetName 項目TableRowEntry （格式） 的 EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="0d038-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0d038-106">語法</span><span class="sxs-lookup"><span data-stu-id="0d038-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0d038-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="0d038-107">Attributes and Elements</span></span>

<span data-ttu-id="0d038-108">下列各節說明屬性、 子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0d038-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0d038-109">屬性</span><span class="sxs-lookup"><span data-stu-id="0d038-109">Attributes</span></span>

<span data-ttu-id="0d038-110">無。</span><span class="sxs-lookup"><span data-stu-id="0d038-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0d038-111">子元素</span><span class="sxs-lookup"><span data-stu-id="0d038-111">Child Elements</span></span>

<span data-ttu-id="0d038-112">無。</span><span class="sxs-lookup"><span data-stu-id="0d038-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0d038-113">父元素</span><span class="sxs-lookup"><span data-stu-id="0d038-113">Parent Elements</span></span>

|<span data-ttu-id="0d038-114">元素</span><span class="sxs-lookup"><span data-stu-id="0d038-114">Element</span></span>|<span data-ttu-id="0d038-115">描述</span><span class="sxs-lookup"><span data-stu-id="0d038-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0d038-116">EntrySelectedBy 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="0d038-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="0d038-117">定義.NET 型別，使用此項目或要使用此項目必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="0d038-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0d038-118">文字值</span><span class="sxs-lookup"><span data-stu-id="0d038-118">Text Value</span></span>

<span data-ttu-id="0d038-119">指定選取項目集的名稱。</span><span class="sxs-lookup"><span data-stu-id="0d038-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="0d038-120">備註</span><span class="sxs-lookup"><span data-stu-id="0d038-120">Remarks</span></span>

<span data-ttu-id="0d038-121">您想要在多個檢視中定義一組所使用的物件時，會通常會使用選取項目集。</span><span class="sxs-lookup"><span data-stu-id="0d038-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="0d038-122">例如，您可能要建立的資料表檢視和相同的物件集的清單檢視。</span><span class="sxs-lookup"><span data-stu-id="0d038-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="0d038-123">如需定義選取項目集的詳細資訊，請參閱[檢視的物件的定義設定](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="0d038-123">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="0d038-124">如果您指定的選取範圍的項目集，您無法指定型別名稱。</span><span class="sxs-lookup"><span data-stu-id="0d038-124">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="0d038-125">如需如何指定.NET 類型的詳細資訊，請參閱[TableRowEntry （格式） 的 EntrySelectedBy TypeName 項目](./typename-element-for-entryselectedby-for-tablecontrol-format.md)。</span><span class="sxs-lookup"><span data-stu-id="0d038-125">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="0d038-126">資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="0d038-126">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0d038-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d038-127">See Also</span></span>

[<span data-ttu-id="0d038-128">EntrySelectedBy 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="0d038-128">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="0d038-129">如需檢視定義物件的集合</span><span class="sxs-lookup"><span data-stu-id="0d038-129">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="0d038-130">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="0d038-130">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="0d038-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="0d038-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
