---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)
description: 設定之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: 4177aace5a6a9374900e7339167c69b531c1e2e7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651668"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="604d6-103">設定之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="604d6-103">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="604d6-104">指定一組觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="604d6-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="604d6-105">當這個集合中的任何型別存在時，就會符合條件，並使用此控制項來顯示該物件。</span><span class="sxs-lookup"><span data-stu-id="604d6-105">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="604d6-106">當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="604d6-106">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="604d6-107">設定元素 (格式) 控制項的設定專案 (格式) 控制項的控制項專案 (格式) CustomEntry 專案的設定 (格式控制項的 CustomControl) 格式 (針對設定 (格式的控制項的 CustomControl 格式) 之 entryselectedby 元素，用於 CustomEntry 的設定 (格式) SelectionCondition (格式的控制項) 之 entryselectedby 專案 (格式的控制項) </span><span class="sxs-lookup"><span data-stu-id="604d6-107">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="604d6-108">語法</span><span class="sxs-lookup"><span data-stu-id="604d6-108">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="604d6-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="604d6-109">Attributes and Elements</span></span>

<span data-ttu-id="604d6-110">下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="604d6-110">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="604d6-111">屬性</span><span class="sxs-lookup"><span data-stu-id="604d6-111">Attributes</span></span>

<span data-ttu-id="604d6-112">無。</span><span class="sxs-lookup"><span data-stu-id="604d6-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="604d6-113">子元素</span><span class="sxs-lookup"><span data-stu-id="604d6-113">Child Elements</span></span>

<span data-ttu-id="604d6-114">無。</span><span class="sxs-lookup"><span data-stu-id="604d6-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="604d6-115">父項目</span><span class="sxs-lookup"><span data-stu-id="604d6-115">Parent Elements</span></span>

|<span data-ttu-id="604d6-116">元素</span><span class="sxs-lookup"><span data-stu-id="604d6-116">Element</span></span>|<span data-ttu-id="604d6-117">描述</span><span class="sxs-lookup"><span data-stu-id="604d6-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="604d6-118">設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="604d6-118">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="604d6-119">定義必須存在才能使用控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="604d6-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="604d6-120">文字值</span><span class="sxs-lookup"><span data-stu-id="604d6-120">Text Value</span></span>

<span data-ttu-id="604d6-121">指定選項群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="604d6-121">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="604d6-122">備註</span><span class="sxs-lookup"><span data-stu-id="604d6-122">Remarks</span></span>

<span data-ttu-id="604d6-123">選項群組是一組通用的 .NET 物件，可供格式化檔案所定義的任何視圖使用。</span><span class="sxs-lookup"><span data-stu-id="604d6-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="604d6-124">如需有關建立和參考選取集的詳細資訊，請參閱 [定義物件集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="604d6-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="604d6-125">選取條件可以指定選擇集或 .NET 類型，但無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="604d6-125">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="604d6-126">如需如何使用選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="604d6-126">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="604d6-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="604d6-127">See Also</span></span>

[<span data-ttu-id="604d6-128">設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="604d6-128">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="604d6-129">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="604d6-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="604d6-130">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="604d6-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="604d6-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="604d6-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
