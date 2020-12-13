---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)
description: EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: 0c9372113a79f75cfbda67acf869164fde894ee3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651595"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="dc4a7-103">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dc4a7-103">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="dc4a7-104">指定一組觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="dc4a7-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="dc4a7-105">當此集合中的任何類型存在時，就會符合條件。</span><span class="sxs-lookup"><span data-stu-id="dc4a7-105">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="dc4a7-106">Configuration Element DefaultSettings 元素 (格式) EnumerableExpansions 元素 (格式) EnumerableExpansions 元素 (格式) EnumerableExpansion 的 SelectionCondition (格式) 之 entryselectedby 專案 EnumerableExpansion (格式) SelectionSetName 專案 SelectionCondition for 之 entryselectedby 的 EnumerableExpansion (格式) </span><span class="sxs-lookup"><span data-stu-id="dc4a7-106">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dc4a7-107">語法</span><span class="sxs-lookup"><span data-stu-id="dc4a7-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dc4a7-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dc4a7-108">Attributes and Elements</span></span>

<span data-ttu-id="dc4a7-109">下列各節描述專案的屬性、子項目和父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="dc4a7-109">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dc4a7-110">屬性</span><span class="sxs-lookup"><span data-stu-id="dc4a7-110">Attributes</span></span>

<span data-ttu-id="dc4a7-111">無。</span><span class="sxs-lookup"><span data-stu-id="dc4a7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dc4a7-112">子元素</span><span class="sxs-lookup"><span data-stu-id="dc4a7-112">Child Elements</span></span>

<span data-ttu-id="dc4a7-113">無。</span><span class="sxs-lookup"><span data-stu-id="dc4a7-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dc4a7-114">父項目</span><span class="sxs-lookup"><span data-stu-id="dc4a7-114">Parent Elements</span></span>

|<span data-ttu-id="dc4a7-115">元素</span><span class="sxs-lookup"><span data-stu-id="dc4a7-115">Element</span></span>|<span data-ttu-id="dc4a7-116">描述</span><span class="sxs-lookup"><span data-stu-id="dc4a7-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dc4a7-117">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dc4a7-117">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="dc4a7-118">定義必須存在才能展開這個定義之集合物件的條件。</span><span class="sxs-lookup"><span data-stu-id="dc4a7-118">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dc4a7-119">文字值</span><span class="sxs-lookup"><span data-stu-id="dc4a7-119">Text Value</span></span>

<span data-ttu-id="dc4a7-120">指定選項群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="dc4a7-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="dc4a7-121">備註</span><span class="sxs-lookup"><span data-stu-id="dc4a7-121">Remarks</span></span>

<span data-ttu-id="dc4a7-122">選取條件可以指定選擇集或 .NET 類型，但無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="dc4a7-122">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="dc4a7-123">如需如何使用選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="dc4a7-123">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="dc4a7-124">選項群組是一組通用的 .NET 物件，可供格式化檔案所定義的任何視圖使用。</span><span class="sxs-lookup"><span data-stu-id="dc4a7-124">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="dc4a7-125">如需有關建立和參考選取集的詳細資訊，請參閱 [定義選取集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="dc4a7-125">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dc4a7-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc4a7-126">See Also</span></span>

[<span data-ttu-id="dc4a7-127">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="dc4a7-127">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="dc4a7-128">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dc4a7-128">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="dc4a7-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="dc4a7-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
