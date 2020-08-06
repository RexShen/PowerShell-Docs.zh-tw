---
title: ListControl (格式) 的之 entryselectedby 的 SelectionSetName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4315d81da4ceeb7a5b171087434ae15fb09e6592
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785263"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="5240f-102">ListControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5240f-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="5240f-103">為清單專案指定一組 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="5240f-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="5240f-104">可以為專案指定的選擇集數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="5240f-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="5240f-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListEntries 專案 (格式) ListEntry 專案 (格式) 之 entryselectedby 元素用於 ListEntry (格式) SelectionSetName 元素 (</span><span class="sxs-lookup"><span data-stu-id="5240f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5240f-106">語法</span><span class="sxs-lookup"><span data-stu-id="5240f-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5240f-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5240f-107">Attributes and Elements</span></span>

<span data-ttu-id="5240f-108">下列各節描述元素的屬性、子專案和父項目 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="5240f-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5240f-109">屬性</span><span class="sxs-lookup"><span data-stu-id="5240f-109">Attributes</span></span>

<span data-ttu-id="5240f-110">無。</span><span class="sxs-lookup"><span data-stu-id="5240f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5240f-111">子元素</span><span class="sxs-lookup"><span data-stu-id="5240f-111">Child Elements</span></span>

<span data-ttu-id="5240f-112">無。</span><span class="sxs-lookup"><span data-stu-id="5240f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5240f-113">父項目</span><span class="sxs-lookup"><span data-stu-id="5240f-113">Parent Elements</span></span>

|<span data-ttu-id="5240f-114">元素</span><span class="sxs-lookup"><span data-stu-id="5240f-114">Element</span></span>|<span data-ttu-id="5240f-115">描述</span><span class="sxs-lookup"><span data-stu-id="5240f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5240f-116">ListEntry (格式的之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="5240f-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="5240f-117">定義使用此清單專案的 .NET 類型，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="5240f-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5240f-118">文字值</span><span class="sxs-lookup"><span data-stu-id="5240f-118">Text Value</span></span>

<span data-ttu-id="5240f-119">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="5240f-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="5240f-120">備註</span><span class="sxs-lookup"><span data-stu-id="5240f-120">Remarks</span></span>

<span data-ttu-id="5240f-121">每個清單專案都必須定義至少一個型別名稱、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="5240f-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="5240f-122">當您想要定義多個視圖中使用的一組物件時，通常會使用選取範圍集。</span><span class="sxs-lookup"><span data-stu-id="5240f-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="5240f-123">例如，您可能會想要建立一組相同物件的資料表視圖和清單視圖。</span><span class="sxs-lookup"><span data-stu-id="5240f-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="5240f-124">如需定義選取集的詳細資訊，請參閱[定義視圖的物件集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="5240f-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="5240f-125">如需清單視圖之元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="5240f-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="5240f-126">範例</span><span class="sxs-lookup"><span data-stu-id="5240f-126">Example</span></span>

<span data-ttu-id="5240f-127">下列範例示範如何指定清單視圖專案的選擇集。</span><span class="sxs-lookup"><span data-stu-id="5240f-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="5240f-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5240f-128">See Also</span></span>

[<span data-ttu-id="5240f-129">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="5240f-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="5240f-130">ListEntry (格式的之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="5240f-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="5240f-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="5240f-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
