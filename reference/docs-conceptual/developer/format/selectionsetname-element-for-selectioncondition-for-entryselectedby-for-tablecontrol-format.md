---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)
description: TableControl 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: 2fb09e27eef1ce5d6e864c72edb595817d91f729
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655045"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="3a2fe-103">TableControl 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3a2fe-103">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="3a2fe-104">指定一組觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="3a2fe-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="3a2fe-105">當這個集合中的任何型別存在時，就會符合條件，並且會使用資料表視圖的這項定義來顯示該物件。</span><span class="sxs-lookup"><span data-stu-id="3a2fe-105">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="3a2fe-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) TableRowEntries 元素 (格式) TableRowEntry 專案 (格式) 之 entryselectedby 專案 (格式) 專案 (格式) TableRowEntry 專案的 SelectionCondition (格式) 之 entryselectedby 專案 TableRowEntry SelectionSetName 的 SelectionCondition 格式</span><span class="sxs-lookup"><span data-stu-id="3a2fe-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3a2fe-107">語法</span><span class="sxs-lookup"><span data-stu-id="3a2fe-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3a2fe-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3a2fe-108">Attributes and Elements</span></span>

<span data-ttu-id="3a2fe-109">下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="3a2fe-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3a2fe-110">屬性</span><span class="sxs-lookup"><span data-stu-id="3a2fe-110">Attributes</span></span>

<span data-ttu-id="3a2fe-111">無。</span><span class="sxs-lookup"><span data-stu-id="3a2fe-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3a2fe-112">子元素</span><span class="sxs-lookup"><span data-stu-id="3a2fe-112">Child Elements</span></span>

<span data-ttu-id="3a2fe-113">無。</span><span class="sxs-lookup"><span data-stu-id="3a2fe-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3a2fe-114">父項目</span><span class="sxs-lookup"><span data-stu-id="3a2fe-114">Parent Elements</span></span>

|<span data-ttu-id="3a2fe-115">元素</span><span class="sxs-lookup"><span data-stu-id="3a2fe-115">Element</span></span>|<span data-ttu-id="3a2fe-116">描述</span><span class="sxs-lookup"><span data-stu-id="3a2fe-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3a2fe-117">適用于之 entryselectedby 的 TableRowEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="3a2fe-117">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="3a2fe-118">定義必須存在的條件，才能用於此資料表視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="3a2fe-118">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3a2fe-119">文字值</span><span class="sxs-lookup"><span data-stu-id="3a2fe-119">Text Value</span></span>

<span data-ttu-id="3a2fe-120">指定選項群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="3a2fe-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="3a2fe-121">備註</span><span class="sxs-lookup"><span data-stu-id="3a2fe-121">Remarks</span></span>

<span data-ttu-id="3a2fe-122">選取條件可以指定選擇集或 .NET 類型，但無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="3a2fe-122">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="3a2fe-123">如需如何使用選取條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="3a2fe-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="3a2fe-124">選項群組是一組通用的 .NET 物件，可供格式化檔案所定義的任何視圖使用。</span><span class="sxs-lookup"><span data-stu-id="3a2fe-124">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="3a2fe-125">如需有關建立和參考選取集的詳細資訊，請參閱 [定義物件集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="3a2fe-125">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="3a2fe-126">如需有關廣泛視圖之其他元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="3a2fe-126">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3a2fe-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a2fe-127">See Also</span></span>

[<span data-ttu-id="3a2fe-128">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="3a2fe-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="3a2fe-129">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="3a2fe-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="3a2fe-130">TableRowEntry (格式之之 entryselectedby 的 SelectionCondition 的 TypeName 元素) </span><span class="sxs-lookup"><span data-stu-id="3a2fe-130">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="3a2fe-131">適用于之 entryselectedby 的 TableRowEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="3a2fe-131">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="3a2fe-132">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="3a2fe-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
