---
title: WideControl （格式） 的 EntrySelectedBy SelectionSetName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064013"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="c8424-102">WideControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c8424-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="c8424-103">指定一組定義的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="c8424-103">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="c8424-104">每當顯示下列其中一個這些物件，則會使用定義。</span><span class="sxs-lookup"><span data-stu-id="c8424-104">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="c8424-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry 項目 （格式） EntrySelectedBy 項目用於 WideEntry （格式） SelectionSetName 元素WideEntry （格式） 的 EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="c8424-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c8424-106">語法</span><span class="sxs-lookup"><span data-stu-id="c8424-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c8424-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c8424-107">Attributes and Elements</span></span>

<span data-ttu-id="c8424-108">下列各節說明屬性、 子項目和父項目`SelectionSetName`項目。</span><span class="sxs-lookup"><span data-stu-id="c8424-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c8424-109">屬性</span><span class="sxs-lookup"><span data-stu-id="c8424-109">Attributes</span></span>

<span data-ttu-id="c8424-110">無。</span><span class="sxs-lookup"><span data-stu-id="c8424-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c8424-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c8424-111">Child Elements</span></span>

<span data-ttu-id="c8424-112">無。</span><span class="sxs-lookup"><span data-stu-id="c8424-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c8424-113">父項目</span><span class="sxs-lookup"><span data-stu-id="c8424-113">Parent Elements</span></span>

|<span data-ttu-id="c8424-114">項目</span><span class="sxs-lookup"><span data-stu-id="c8424-114">Element</span></span>|<span data-ttu-id="c8424-115">描述</span><span class="sxs-lookup"><span data-stu-id="c8424-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c8424-116">EntrySelectedBy WideEntry （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="c8424-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="c8424-117">定義.NET 型別，使用此寬的項目或要使用此項目必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="c8424-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c8424-118">文字值</span><span class="sxs-lookup"><span data-stu-id="c8424-118">Text Value</span></span>

<span data-ttu-id="c8424-119">指定選取項目集的名稱。</span><span class="sxs-lookup"><span data-stu-id="c8424-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="c8424-120">備註</span><span class="sxs-lookup"><span data-stu-id="c8424-120">Remarks</span></span>

<span data-ttu-id="c8424-121">每個定義必須指定一個型別名稱、 選取項目集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="c8424-121">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="c8424-122">您想要在多個檢視中定義一組所使用的物件時，會通常會使用選取項目集。</span><span class="sxs-lookup"><span data-stu-id="c8424-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="c8424-123">例如，您可能要建立的資料表檢視和相同的物件集的清單檢視。</span><span class="sxs-lookup"><span data-stu-id="c8424-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="c8424-124">如需定義選取項目集的詳細資訊，請參閱[定義設定的物件檢視](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="c8424-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="c8424-125">寬型檢視的其他元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="c8424-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c8424-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8424-126">See Also</span></span>

[<span data-ttu-id="c8424-127">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="c8424-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="c8424-128">定義選取範圍</span><span class="sxs-lookup"><span data-stu-id="c8424-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="c8424-129">EntrySelectedBy WideEntry （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="c8424-129">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="c8424-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="c8424-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
