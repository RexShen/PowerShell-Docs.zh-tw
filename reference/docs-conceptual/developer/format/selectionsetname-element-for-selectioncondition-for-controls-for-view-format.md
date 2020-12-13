---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)
description: 檢視之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: b23ee5310d415cf287bf99c73b1173f70ae15f4c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651636"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="c0978-103">檢視之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c0978-103">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="c0978-104">指定一組觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="c0978-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="c0978-105">當這個集合中的任何類型存在時，就會符合條件，並使用此控制項來顯示該物件。</span><span class="sxs-lookup"><span data-stu-id="c0978-105">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="c0978-106">當定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="c0978-106">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="c0978-107">設定元素 (格式) ViewDefinitions 元素 (格式) View 專案 (格式) 控制項專案 (格式) 控制項專案 (格式) 控制項控制項的控制項 (格式) CustomEntries 元素，用於控制項的視圖 (格式) 適用于 view 的控制項之 CustomEntries 的 CustomEntry 專案 (格式) 之 entryselectedby 專案 CustomEntry 的控制項視圖 (格式) SelectionCondition 專案的專案 (格式) 之 entryselectedby 專案的 SelectionSetName 專案 (格式) 的控制項</span><span class="sxs-lookup"><span data-stu-id="c0978-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c0978-108">語法</span><span class="sxs-lookup"><span data-stu-id="c0978-108">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c0978-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c0978-109">Attributes and Elements</span></span>

<span data-ttu-id="c0978-110">下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="c0978-110">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c0978-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c0978-111">Attributes</span></span>

<span data-ttu-id="c0978-112">無。</span><span class="sxs-lookup"><span data-stu-id="c0978-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c0978-113">子元素</span><span class="sxs-lookup"><span data-stu-id="c0978-113">Child Elements</span></span>

<span data-ttu-id="c0978-114">無。</span><span class="sxs-lookup"><span data-stu-id="c0978-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c0978-115">父項目</span><span class="sxs-lookup"><span data-stu-id="c0978-115">Parent Elements</span></span>

|<span data-ttu-id="c0978-116">元素</span><span class="sxs-lookup"><span data-stu-id="c0978-116">Element</span></span>|<span data-ttu-id="c0978-117">描述</span><span class="sxs-lookup"><span data-stu-id="c0978-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0978-118">檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c0978-118">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="c0978-119">定義必須存在才能使用控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="c0978-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c0978-120">文字值</span><span class="sxs-lookup"><span data-stu-id="c0978-120">Text Value</span></span>

<span data-ttu-id="c0978-121">指定選項群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="c0978-121">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="c0978-122">備註</span><span class="sxs-lookup"><span data-stu-id="c0978-122">Remarks</span></span>

<span data-ttu-id="c0978-123">選項群組是一組通用的 .NET 物件，可供格式化檔案所定義的任何視圖使用。</span><span class="sxs-lookup"><span data-stu-id="c0978-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="c0978-124">如需有關建立和參考選取集的詳細資訊，請參閱 [定義選取集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="c0978-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="c0978-125">選取條件可以指定選擇集或 .NET 類型，但無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="c0978-125">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="c0978-126">如需如何使用選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c0978-126">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c0978-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0978-127">See Also</span></span>

[<span data-ttu-id="c0978-128">檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c0978-128">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="c0978-129">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="c0978-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c0978-130">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="c0978-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="c0978-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="c0978-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
