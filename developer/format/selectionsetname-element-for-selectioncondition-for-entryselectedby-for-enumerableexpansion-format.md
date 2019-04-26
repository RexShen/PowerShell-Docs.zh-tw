---
title: 針對 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063855"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="f4db9-102">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="f4db9-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="f4db9-103">指定的觸發條件的.NET 型別集。</span><span class="sxs-lookup"><span data-stu-id="f4db9-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="f4db9-104">當有任何在這組型別時，即符合條件。</span><span class="sxs-lookup"><span data-stu-id="f4db9-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="f4db9-105">組態項目 DefaultSettings 項目 （格式） EnumerableExpansions 項目 （格式） EnumerableExpansions 項目 （格式） EntrySelectedBy 項目為 EntrySelectedBy EnumerableExpansion （格式） SelectionCondition 項目針對 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition EnumerableExpansion （格式） SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="f4db9-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f4db9-106">語法</span><span class="sxs-lookup"><span data-stu-id="f4db9-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f4db9-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f4db9-107">Attributes and Elements</span></span>

<span data-ttu-id="f4db9-108">下列各節說明屬性、 子項目和父項目`SelectionSetName`項目。</span><span class="sxs-lookup"><span data-stu-id="f4db9-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f4db9-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f4db9-109">Attributes</span></span>

<span data-ttu-id="f4db9-110">無。</span><span class="sxs-lookup"><span data-stu-id="f4db9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f4db9-111">子元素</span><span class="sxs-lookup"><span data-stu-id="f4db9-111">Child Elements</span></span>

<span data-ttu-id="f4db9-112">無。</span><span class="sxs-lookup"><span data-stu-id="f4db9-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f4db9-113">父項目</span><span class="sxs-lookup"><span data-stu-id="f4db9-113">Parent Elements</span></span>

|<span data-ttu-id="f4db9-114">項目</span><span class="sxs-lookup"><span data-stu-id="f4db9-114">Element</span></span>|<span data-ttu-id="f4db9-115">描述</span><span class="sxs-lookup"><span data-stu-id="f4db9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f4db9-116">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="f4db9-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="f4db9-117">定義必須存在以展開此定義的集合物件的條件。</span><span class="sxs-lookup"><span data-stu-id="f4db9-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f4db9-118">文字值</span><span class="sxs-lookup"><span data-stu-id="f4db9-118">Text Value</span></span>

<span data-ttu-id="f4db9-119">指定選取項目集的名稱。</span><span class="sxs-lookup"><span data-stu-id="f4db9-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="f4db9-120">備註</span><span class="sxs-lookup"><span data-stu-id="f4db9-120">Remarks</span></span>

<span data-ttu-id="f4db9-121">選取條件可以指定的選取項目集或.NET 類型，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="f4db9-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="f4db9-122">如需如何使用選擇條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f4db9-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f4db9-123">選取項目集是常見的.NET 物件，可供任何檢視中定義的格式化檔案群組。</span><span class="sxs-lookup"><span data-stu-id="f4db9-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="f4db9-124">如需有關建立及參考選取項目集的詳細資訊，請參閱 <<c0> [ 定義的選取項目設定](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="f4db9-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f4db9-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4db9-125">See Also</span></span>

[<span data-ttu-id="f4db9-126">定義選取範圍</span><span class="sxs-lookup"><span data-stu-id="f4db9-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="f4db9-127">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="f4db9-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="f4db9-128">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="f4db9-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
