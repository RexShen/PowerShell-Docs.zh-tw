---
title: ListControl （格式） 的 EntrySelectedBy SelectionSetName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075557"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="c9666-102">ListControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c9666-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="c9666-103">指定一組.NET 物件清單項目。</span><span class="sxs-lookup"><span data-stu-id="c9666-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="c9666-104">可供指定的項目選取項目集的數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="c9666-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="c9666-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 （格式） ListEntry 項目 （格式） EntrySelectedBy 項目用於 ListEntry （格式） SelectionSetName 元素ListEntry （格式） 的 EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="c9666-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c9666-106">語法</span><span class="sxs-lookup"><span data-stu-id="c9666-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c9666-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c9666-107">Attributes and Elements</span></span>

<span data-ttu-id="c9666-108">下列各節說明屬性、 子項目和父項目`SelectionSetName`項目。</span><span class="sxs-lookup"><span data-stu-id="c9666-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c9666-109">屬性</span><span class="sxs-lookup"><span data-stu-id="c9666-109">Attributes</span></span>

<span data-ttu-id="c9666-110">無。</span><span class="sxs-lookup"><span data-stu-id="c9666-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c9666-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c9666-111">Child Elements</span></span>

<span data-ttu-id="c9666-112">無。</span><span class="sxs-lookup"><span data-stu-id="c9666-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c9666-113">父項目</span><span class="sxs-lookup"><span data-stu-id="c9666-113">Parent Elements</span></span>

|<span data-ttu-id="c9666-114">項目</span><span class="sxs-lookup"><span data-stu-id="c9666-114">Element</span></span>|<span data-ttu-id="c9666-115">描述</span><span class="sxs-lookup"><span data-stu-id="c9666-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c9666-116">EntrySelectedBy ListEntry （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="c9666-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="c9666-117">定義.NET 型別，使用此清單項目或要使用此項目必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="c9666-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c9666-118">文字值</span><span class="sxs-lookup"><span data-stu-id="c9666-118">Text Value</span></span>

<span data-ttu-id="c9666-119">指定選取項目集的名稱。</span><span class="sxs-lookup"><span data-stu-id="c9666-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="c9666-120">備註</span><span class="sxs-lookup"><span data-stu-id="c9666-120">Remarks</span></span>

<span data-ttu-id="c9666-121">每個清單項目必須至少一個型別名稱、 選取項目集或選擇條件的定義。</span><span class="sxs-lookup"><span data-stu-id="c9666-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="c9666-122">您想要在多個檢視中定義一組所使用的物件時，會通常會使用選取項目集。</span><span class="sxs-lookup"><span data-stu-id="c9666-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="c9666-123">例如，您可能要建立的資料表檢視和相同的物件集的清單檢視。</span><span class="sxs-lookup"><span data-stu-id="c9666-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="c9666-124">如需定義選取項目集的詳細資訊，請參閱[檢視的物件的定義設定](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="c9666-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="c9666-125">清單檢視元件的相關資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="c9666-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c9666-126">範例</span><span class="sxs-lookup"><span data-stu-id="c9666-126">Example</span></span>

<span data-ttu-id="c9666-127">下列範例示範如何指定設定項目清單檢視的選取範圍。</span><span class="sxs-lookup"><span data-stu-id="c9666-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="c9666-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9666-128">See Also</span></span>

[<span data-ttu-id="c9666-129">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="c9666-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c9666-130">EntrySelectedBy ListEntry （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="c9666-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="c9666-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="c9666-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
