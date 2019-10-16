---
title: ListControl 之之 entryselectedby 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361997"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="b4db5-102">ListControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b4db5-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="b4db5-103">為清單專案指定一組 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="b4db5-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="b4db5-104">可以為專案指定的選擇集數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="b4db5-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="b4db5-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（格式） ListEntries 元素（格式） ListEntry 元素（格式）之 entryselectedby 元素（代表的 ListEntry （格式） SelectionSetName 元素）ListEntry 的之 entryselectedby （格式）</span><span class="sxs-lookup"><span data-stu-id="b4db5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b4db5-106">語法</span><span class="sxs-lookup"><span data-stu-id="b4db5-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b4db5-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="b4db5-107">Attributes and Elements</span></span>

<span data-ttu-id="b4db5-108">下列各節描述 `SelectionSetName` 元素的屬性、子專案和父元素。</span><span class="sxs-lookup"><span data-stu-id="b4db5-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b4db5-109">屬性</span><span class="sxs-lookup"><span data-stu-id="b4db5-109">Attributes</span></span>

<span data-ttu-id="b4db5-110">無。</span><span class="sxs-lookup"><span data-stu-id="b4db5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b4db5-111">子元素</span><span class="sxs-lookup"><span data-stu-id="b4db5-111">Child Elements</span></span>

<span data-ttu-id="b4db5-112">無。</span><span class="sxs-lookup"><span data-stu-id="b4db5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b4db5-113">父元素</span><span class="sxs-lookup"><span data-stu-id="b4db5-113">Parent Elements</span></span>

|<span data-ttu-id="b4db5-114">元素</span><span class="sxs-lookup"><span data-stu-id="b4db5-114">Element</span></span>|<span data-ttu-id="b4db5-115">描述</span><span class="sxs-lookup"><span data-stu-id="b4db5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4db5-116">ListEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b4db5-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="b4db5-117">定義使用此清單專案的 .NET 類型，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="b4db5-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b4db5-118">文字值</span><span class="sxs-lookup"><span data-stu-id="b4db5-118">Text Value</span></span>

<span data-ttu-id="b4db5-119">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="b4db5-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4db5-120">備註</span><span class="sxs-lookup"><span data-stu-id="b4db5-120">Remarks</span></span>

<span data-ttu-id="b4db5-121">每個清單專案都必須定義至少一個型別名稱、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="b4db5-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="b4db5-122">當您想要定義多個視圖中使用的一組物件時，通常會使用選取範圍集。</span><span class="sxs-lookup"><span data-stu-id="b4db5-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="b4db5-123">例如，您可能會想要建立一組相同物件的資料表視圖和清單視圖。</span><span class="sxs-lookup"><span data-stu-id="b4db5-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="b4db5-124">如需定義選取集的詳細資訊，請參閱[定義視圖的物件集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="b4db5-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="b4db5-125">如需清單視圖之元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="b4db5-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b4db5-126">範例</span><span class="sxs-lookup"><span data-stu-id="b4db5-126">Example</span></span>

<span data-ttu-id="b4db5-127">下列範例示範如何指定清單視圖專案的選擇集。</span><span class="sxs-lookup"><span data-stu-id="b4db5-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="b4db5-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4db5-128">See Also</span></span>

[<span data-ttu-id="b4db5-129">建立清單視圖</span><span class="sxs-lookup"><span data-stu-id="b4db5-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="b4db5-130">ListEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b4db5-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="b4db5-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="b4db5-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
