---
ms.date: 09/13/2016
ms.topic: reference
title: ListEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)
description: ListEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: f3193799e67706eb07f0fe1c2cd42cce83f7af57
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651540"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="8097f-103">ListEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8097f-103">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="8097f-104">指定一組觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="8097f-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="8097f-105">當這個集合中的任何類型存在時，就會符合條件，並且使用清單視圖的這項定義來顯示該物件。</span><span class="sxs-lookup"><span data-stu-id="8097f-105">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="8097f-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 元素 (格式) ListEntries 元素 (格式) ListEntry 專案 (格式) 之 entryselectedby 專案 (格式) 專案 (格式) ListEntry 專案的 SelectionCondition (格式) 之 entryselectedby 專案 ListEntry SelectionSetName 的 SelectionCondition 格式</span><span class="sxs-lookup"><span data-stu-id="8097f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8097f-107">語法</span><span class="sxs-lookup"><span data-stu-id="8097f-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8097f-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8097f-108">Attributes and Elements</span></span>

<span data-ttu-id="8097f-109">下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="8097f-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8097f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="8097f-110">Attributes</span></span>

<span data-ttu-id="8097f-111">無。</span><span class="sxs-lookup"><span data-stu-id="8097f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8097f-112">子元素</span><span class="sxs-lookup"><span data-stu-id="8097f-112">Child Elements</span></span>

<span data-ttu-id="8097f-113">無。</span><span class="sxs-lookup"><span data-stu-id="8097f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8097f-114">父項目</span><span class="sxs-lookup"><span data-stu-id="8097f-114">Parent Elements</span></span>

|<span data-ttu-id="8097f-115">元素</span><span class="sxs-lookup"><span data-stu-id="8097f-115">Element</span></span>|<span data-ttu-id="8097f-116">描述</span><span class="sxs-lookup"><span data-stu-id="8097f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8097f-117">適用于之 entryselectedby 的 ListEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="8097f-117">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="8097f-118">定義必須存在的條件，才能使用此清單視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="8097f-118">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8097f-119">文字值</span><span class="sxs-lookup"><span data-stu-id="8097f-119">Text Value</span></span>

<span data-ttu-id="8097f-120">指定選項群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="8097f-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="8097f-121">備註</span><span class="sxs-lookup"><span data-stu-id="8097f-121">Remarks</span></span>

<span data-ttu-id="8097f-122">選取條件可以指定選擇集或 .NET 類型，但無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="8097f-122">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="8097f-123">如需如何使用選取條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="8097f-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="8097f-124">選項群組是一組通用的 .NET 物件，可供格式化檔案所定義的任何視圖使用。</span><span class="sxs-lookup"><span data-stu-id="8097f-124">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="8097f-125">如需有關建立和參考選取集的詳細資訊，請參閱 [定義物件集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="8097f-125">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="8097f-126">如需清單視圖之其他元件的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="8097f-126">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8097f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8097f-127">See Also</span></span>

[<span data-ttu-id="8097f-128">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="8097f-128">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="8097f-129">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="8097f-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="8097f-130">適用于之 entryselectedby 的 ListEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="8097f-130">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="8097f-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="8097f-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
