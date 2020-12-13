---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之 CustomControl 的 SelectionCondition 的 SelectionSetName 元素 (格式)
description: 檢視之 CustomControl 的 SelectionCondition 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: 839032048739e529057d7066fb3bc6aa2fbc5037
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651606"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="cf1ef-103">檢視之 CustomControl 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="cf1ef-103">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="cf1ef-104">指定一組觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="cf1ef-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="cf1ef-105">當這個集合中的任何類型存在時，就會符合條件，並使用此控制項來顯示該物件。</span><span class="sxs-lookup"><span data-stu-id="cf1ef-105">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="cf1ef-106">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="cf1ef-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="cf1ef-107">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 專案 (格式) CustomEntries 專案 (格式) 專案 (格式) CustomEntry 專案 (格式) CustomEntries 專案格式之 entryselectedby 元素</span><span class="sxs-lookup"><span data-stu-id="cf1ef-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cf1ef-108">語法</span><span class="sxs-lookup"><span data-stu-id="cf1ef-108">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cf1ef-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cf1ef-109">Attributes and Elements</span></span>

<span data-ttu-id="cf1ef-110">下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="cf1ef-110">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cf1ef-111">屬性</span><span class="sxs-lookup"><span data-stu-id="cf1ef-111">Attributes</span></span>

<span data-ttu-id="cf1ef-112">無。</span><span class="sxs-lookup"><span data-stu-id="cf1ef-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cf1ef-113">子元素</span><span class="sxs-lookup"><span data-stu-id="cf1ef-113">Child Elements</span></span>

<span data-ttu-id="cf1ef-114">無。</span><span class="sxs-lookup"><span data-stu-id="cf1ef-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cf1ef-115">父項目</span><span class="sxs-lookup"><span data-stu-id="cf1ef-115">Parent Elements</span></span>

|<span data-ttu-id="cf1ef-116">元素</span><span class="sxs-lookup"><span data-stu-id="cf1ef-116">Element</span></span>|<span data-ttu-id="cf1ef-117">描述</span><span class="sxs-lookup"><span data-stu-id="cf1ef-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cf1ef-118">適用于 CustomControl 的之 entryselectedby SelectionCondition 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="cf1ef-118">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="cf1ef-119">定義必須存在才能使用控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="cf1ef-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cf1ef-120">文字值</span><span class="sxs-lookup"><span data-stu-id="cf1ef-120">Text Value</span></span>

<span data-ttu-id="cf1ef-121">指定選項群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="cf1ef-121">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="cf1ef-122">備註</span><span class="sxs-lookup"><span data-stu-id="cf1ef-122">Remarks</span></span>

<span data-ttu-id="cf1ef-123">選項群組是一組通用的 .NET 物件，可供格式化檔案所定義的任何視圖使用。</span><span class="sxs-lookup"><span data-stu-id="cf1ef-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="cf1ef-124">如需有關建立和參考選取集的詳細資訊，請參閱 [定義物件集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="cf1ef-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="cf1ef-125">選取條件可以指定選擇集或 .NET 類型，但無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="cf1ef-125">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="cf1ef-126">如需如何使用選取條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="cf1ef-126">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cf1ef-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf1ef-127">See Also</span></span>

[<span data-ttu-id="cf1ef-128">適用于 CustomControl 的之 entryselectedby SelectionCondition 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="cf1ef-128">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="cf1ef-129">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="cf1ef-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="cf1ef-130">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="cf1ef-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="cf1ef-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="cf1ef-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
