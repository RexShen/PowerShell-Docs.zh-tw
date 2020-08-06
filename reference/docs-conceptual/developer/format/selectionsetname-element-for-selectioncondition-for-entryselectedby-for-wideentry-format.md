---
title: WideEntry (格式) 的之 entryselectedby 之 SelectionCondition 的 SelectionSetName 元素Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 44c88ce75ae485e1c48ceb08bfd12f739a632996
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787439"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="9317b-102">WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9317b-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="9317b-103">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="9317b-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="9317b-104">當此集合中的任何類型都存在時，就會符合條件，並使用此寬視圖的定義來顯示該物件。</span><span class="sxs-lookup"><span data-stu-id="9317b-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="9317b-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 專案 (格式) WideEntries 專案 (格式) WideEntry 專案 (格式) 之 entryselectedby 元素（WideEntry 的 SelectionCondition (format) 之 entryselectedby 元素，WideEntry for SelectionSetName for SelectionCondition (format) </span><span class="sxs-lookup"><span data-stu-id="9317b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9317b-106">語法</span><span class="sxs-lookup"><span data-stu-id="9317b-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9317b-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9317b-107">Attributes and Elements</span></span>

<span data-ttu-id="9317b-108">下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="9317b-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9317b-109">屬性</span><span class="sxs-lookup"><span data-stu-id="9317b-109">Attributes</span></span>

<span data-ttu-id="9317b-110">無。</span><span class="sxs-lookup"><span data-stu-id="9317b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9317b-111">子元素</span><span class="sxs-lookup"><span data-stu-id="9317b-111">Child Elements</span></span>

<span data-ttu-id="9317b-112">無。</span><span class="sxs-lookup"><span data-stu-id="9317b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9317b-113">父項目</span><span class="sxs-lookup"><span data-stu-id="9317b-113">Parent Elements</span></span>

|<span data-ttu-id="9317b-114">元素</span><span class="sxs-lookup"><span data-stu-id="9317b-114">Element</span></span>|<span data-ttu-id="9317b-115">描述</span><span class="sxs-lookup"><span data-stu-id="9317b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9317b-116">WideEntry (格式的之 entryselectedby 的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="9317b-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="9317b-117">定義必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="9317b-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9317b-118">文字值</span><span class="sxs-lookup"><span data-stu-id="9317b-118">Text Value</span></span>

<span data-ttu-id="9317b-119">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="9317b-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="9317b-120">備註</span><span class="sxs-lookup"><span data-stu-id="9317b-120">Remarks</span></span>

<span data-ttu-id="9317b-121">選取條件可以指定選擇集或 .NET 類型，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="9317b-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="9317b-122">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="9317b-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="9317b-123">選取範圍是一組通用的 .NET 物件，可供格式設定檔案定義的任何視圖使用。</span><span class="sxs-lookup"><span data-stu-id="9317b-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="9317b-124">如需建立和參考選取集的詳細資訊，請參閱[定義物件集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="9317b-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="9317b-125">如需有關寬視圖之其他元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="9317b-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9317b-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9317b-126">See Also</span></span>

[<span data-ttu-id="9317b-127">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="9317b-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="9317b-128">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="9317b-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9317b-129">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="9317b-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="9317b-130">WideEntry (格式的之 entryselectedby 的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="9317b-130">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="9317b-131">SelectionCondition for 之 entryselectedby for WideEntry (Format 的 TypeName 元素) </span><span class="sxs-lookup"><span data-stu-id="9317b-131">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="9317b-132">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="9317b-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
