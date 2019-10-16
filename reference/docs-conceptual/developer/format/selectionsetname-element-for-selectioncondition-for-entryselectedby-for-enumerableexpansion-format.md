---
title: EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361987"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="a1c4d-102">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a1c4d-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="a1c4d-103">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="a1c4d-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="a1c4d-104">當此集合中的任何類型都存在時，就會符合條件。</span><span class="sxs-lookup"><span data-stu-id="a1c4d-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="a1c4d-105">Configuration 元素的 DefaultSettings 元素（格式） EnumerableExpansions 元素（格式） EnumerableExpansions 專案（格式）之 entryselectedby 元素（用於 EnumerableExpansion 的 SelectionCondition 專案）之 entryselectedby 元素EnumerableExpansion （Format） SelectionCondition for 之 entryselectedby for EnumerableExpansion 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a1c4d-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a1c4d-106">語法</span><span class="sxs-lookup"><span data-stu-id="a1c4d-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a1c4d-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="a1c4d-107">Attributes and Elements</span></span>

<span data-ttu-id="a1c4d-108">下列各節描述 `SelectionSetName` 元素的屬性、子專案和父元素。</span><span class="sxs-lookup"><span data-stu-id="a1c4d-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a1c4d-109">屬性</span><span class="sxs-lookup"><span data-stu-id="a1c4d-109">Attributes</span></span>

<span data-ttu-id="a1c4d-110">無。</span><span class="sxs-lookup"><span data-stu-id="a1c4d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a1c4d-111">子元素</span><span class="sxs-lookup"><span data-stu-id="a1c4d-111">Child Elements</span></span>

<span data-ttu-id="a1c4d-112">無。</span><span class="sxs-lookup"><span data-stu-id="a1c4d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a1c4d-113">父元素</span><span class="sxs-lookup"><span data-stu-id="a1c4d-113">Parent Elements</span></span>

|<span data-ttu-id="a1c4d-114">元素</span><span class="sxs-lookup"><span data-stu-id="a1c4d-114">Element</span></span>|<span data-ttu-id="a1c4d-115">描述</span><span class="sxs-lookup"><span data-stu-id="a1c4d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a1c4d-116">EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a1c4d-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="a1c4d-117">定義必須存在的條件，才能展開這個定義的集合物件。</span><span class="sxs-lookup"><span data-stu-id="a1c4d-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a1c4d-118">文字值</span><span class="sxs-lookup"><span data-stu-id="a1c4d-118">Text Value</span></span>

<span data-ttu-id="a1c4d-119">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="a1c4d-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="a1c4d-120">備註</span><span class="sxs-lookup"><span data-stu-id="a1c4d-120">Remarks</span></span>

<span data-ttu-id="a1c4d-121">選取條件可以指定選擇集或 .NET 類型，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="a1c4d-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="a1c4d-122">如需如何使用選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a1c4d-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a1c4d-123">選取範圍是一組通用的 .NET 物件，可供格式設定檔案定義的任何視圖使用。</span><span class="sxs-lookup"><span data-stu-id="a1c4d-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="a1c4d-124">如需建立和參考選取集的詳細資訊，請參閱[定義選取範圍](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="a1c4d-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a1c4d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1c4d-125">See Also</span></span>

[<span data-ttu-id="a1c4d-126">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="a1c4d-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="a1c4d-127">EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a1c4d-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="a1c4d-128">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="a1c4d-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
