---
title: EnumerableExpansion (格式) 的之 entryselectedby 之 SelectionCondition 的 SelectionSetName 元素Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e18c74bb95c658f2c3e7b7454628f78d523f7609
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787490"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="8ce06-102">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8ce06-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="8ce06-103">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="8ce06-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="8ce06-104">當此集合中的任何類型都存在時，就會符合條件。</span><span class="sxs-lookup"><span data-stu-id="8ce06-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="8ce06-105">Configuration 元素 DefaultSettings 元素 (格式) EnumerableExpansions 元素 (格式) EnumerableExpansions 專案 (格式) EnumerableExpansion (格式) SelectionCondition 元素，之 entryselectedby 的 EnumerableExpansion (格式) SelectionSetName 元素 (</span><span class="sxs-lookup"><span data-stu-id="8ce06-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8ce06-106">語法</span><span class="sxs-lookup"><span data-stu-id="8ce06-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8ce06-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8ce06-107">Attributes and Elements</span></span>

<span data-ttu-id="8ce06-108">下列各節描述元素的屬性、子專案和父項目 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="8ce06-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8ce06-109">屬性</span><span class="sxs-lookup"><span data-stu-id="8ce06-109">Attributes</span></span>

<span data-ttu-id="8ce06-110">無。</span><span class="sxs-lookup"><span data-stu-id="8ce06-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8ce06-111">子元素</span><span class="sxs-lookup"><span data-stu-id="8ce06-111">Child Elements</span></span>

<span data-ttu-id="8ce06-112">無。</span><span class="sxs-lookup"><span data-stu-id="8ce06-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8ce06-113">父項目</span><span class="sxs-lookup"><span data-stu-id="8ce06-113">Parent Elements</span></span>

|<span data-ttu-id="8ce06-114">元素</span><span class="sxs-lookup"><span data-stu-id="8ce06-114">Element</span></span>|<span data-ttu-id="8ce06-115">描述</span><span class="sxs-lookup"><span data-stu-id="8ce06-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8ce06-116">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8ce06-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="8ce06-117">定義必須存在的條件，才能展開這個定義的集合物件。</span><span class="sxs-lookup"><span data-stu-id="8ce06-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8ce06-118">文字值</span><span class="sxs-lookup"><span data-stu-id="8ce06-118">Text Value</span></span>

<span data-ttu-id="8ce06-119">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="8ce06-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="8ce06-120">備註</span><span class="sxs-lookup"><span data-stu-id="8ce06-120">Remarks</span></span>

<span data-ttu-id="8ce06-121">選取條件可以指定選擇集或 .NET 類型，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="8ce06-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="8ce06-122">如需如何使用選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="8ce06-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="8ce06-123">選取範圍是一組通用的 .NET 物件，可供格式設定檔案定義的任何視圖使用。</span><span class="sxs-lookup"><span data-stu-id="8ce06-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="8ce06-124">如需建立和參考選取集的詳細資訊，請參閱[定義選取範圍](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="8ce06-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8ce06-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ce06-125">See Also</span></span>

[<span data-ttu-id="8ce06-126">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="8ce06-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="8ce06-127">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8ce06-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="8ce06-128">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="8ce06-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
