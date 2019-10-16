---
title: EnumerableExpansion 之之 entryselectedby 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368327"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="22613-102">EnumerableExpansion 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="22613-102">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="22613-103">指定由這個定義擴充的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="22613-103">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="22613-104">EnumerableExpansion 的 SelectionSetName （Format）之 entryselectedby 元素的 DefaultSettings 元素（格式） EnumerableExpansions 元素（格式） EnumerableExpansion 元素（格式）之 entryselectedby 元素EnumerableExpansion （格式）</span><span class="sxs-lookup"><span data-stu-id="22613-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="22613-105">語法</span><span class="sxs-lookup"><span data-stu-id="22613-105">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="22613-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="22613-106">Attributes and Elements</span></span>

<span data-ttu-id="22613-107">下列各節說明屬性、子專案，以及 `SelectionSetName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="22613-107">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="22613-108">屬性</span><span class="sxs-lookup"><span data-stu-id="22613-108">Attributes</span></span>

<span data-ttu-id="22613-109">無。</span><span class="sxs-lookup"><span data-stu-id="22613-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="22613-110">子元素</span><span class="sxs-lookup"><span data-stu-id="22613-110">Child Elements</span></span>

<span data-ttu-id="22613-111">無。</span><span class="sxs-lookup"><span data-stu-id="22613-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="22613-112">父元素</span><span class="sxs-lookup"><span data-stu-id="22613-112">Parent Elements</span></span>

|<span data-ttu-id="22613-113">元素</span><span class="sxs-lookup"><span data-stu-id="22613-113">Element</span></span>|<span data-ttu-id="22613-114">描述</span><span class="sxs-lookup"><span data-stu-id="22613-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="22613-115">EnumerableExpansion 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="22613-115">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="22613-116">定義由這個定義展開的 .NET 集合物件。</span><span class="sxs-lookup"><span data-stu-id="22613-116">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="22613-117">文字值</span><span class="sxs-lookup"><span data-stu-id="22613-117">Text Value</span></span>

<span data-ttu-id="22613-118">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="22613-118">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="22613-119">備註</span><span class="sxs-lookup"><span data-stu-id="22613-119">Remarks</span></span>

<span data-ttu-id="22613-120">每個定義都必須指定一或多個類型名稱、選取範圍或選取條件。</span><span class="sxs-lookup"><span data-stu-id="22613-120">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="22613-121">當您想要定義多個視圖中使用的一組物件時，通常會使用選取範圍集。</span><span class="sxs-lookup"><span data-stu-id="22613-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="22613-122">例如，您可能會想要建立一組相同物件的資料表視圖和清單視圖。</span><span class="sxs-lookup"><span data-stu-id="22613-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="22613-123">如需定義選取集的詳細資訊，請參閱[定義視圖的物件集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="22613-123">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="22613-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22613-124">See Also</span></span>

[<span data-ttu-id="22613-125">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="22613-125">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="22613-126">EnumerableExpansion 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="22613-126">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="22613-127">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="22613-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
