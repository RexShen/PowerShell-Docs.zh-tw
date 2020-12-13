---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之 SelectionCondition 的 SelectionSetName 元素 (格式)
description: GroupBy 之 SelectionCondition 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: a4f28c1caba3790718b99f63659cb0cbed8def16
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654998"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="384dd-103">GroupBy 之 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="384dd-103">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="384dd-104">指定一組觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="384dd-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="384dd-105">當這個集合中的任何型別存在時，就會符合條件，並使用此控制項來顯示該物件。</span><span class="sxs-lookup"><span data-stu-id="384dd-105">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="384dd-106">定義如何顯示新的物件群組時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="384dd-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="384dd-107">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 專案的視圖 (格式) CustomEntries 元素用於 GroupBy (格式) 元素用於 CustomEntry 的 groupby (格式) CustomControl 專案用於之 entryselectedby 的 groupby (格式) CustomEntry 專案的 SelectionCondition 的 groupby (格式) 之 entryselectedby 元素</span><span class="sxs-lookup"><span data-stu-id="384dd-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="384dd-108">語法</span><span class="sxs-lookup"><span data-stu-id="384dd-108">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="384dd-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="384dd-109">Attributes and Elements</span></span>

<span data-ttu-id="384dd-110">下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="384dd-110">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="384dd-111">屬性</span><span class="sxs-lookup"><span data-stu-id="384dd-111">Attributes</span></span>

<span data-ttu-id="384dd-112">無。</span><span class="sxs-lookup"><span data-stu-id="384dd-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="384dd-113">子元素</span><span class="sxs-lookup"><span data-stu-id="384dd-113">Child Elements</span></span>

<span data-ttu-id="384dd-114">無。</span><span class="sxs-lookup"><span data-stu-id="384dd-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="384dd-115">父項目</span><span class="sxs-lookup"><span data-stu-id="384dd-115">Parent Elements</span></span>

|<span data-ttu-id="384dd-116">元素</span><span class="sxs-lookup"><span data-stu-id="384dd-116">Element</span></span>|<span data-ttu-id="384dd-117">描述</span><span class="sxs-lookup"><span data-stu-id="384dd-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="384dd-118">GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="384dd-118">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="384dd-119">定義必須存在才能使用控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="384dd-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="384dd-120">文字值</span><span class="sxs-lookup"><span data-stu-id="384dd-120">Text Value</span></span>

<span data-ttu-id="384dd-121">指定選項群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="384dd-121">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="384dd-122">備註</span><span class="sxs-lookup"><span data-stu-id="384dd-122">Remarks</span></span>

<span data-ttu-id="384dd-123">選項群組是一組通用的 .NET 物件，可供格式化檔案所定義的任何視圖使用。</span><span class="sxs-lookup"><span data-stu-id="384dd-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="384dd-124">如需有關建立和參考選取集的詳細資訊，請參閱 [定義選取集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="384dd-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="384dd-125">當指定這個專案時，您無法指定 [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="384dd-125">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="384dd-126">如需定義選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="384dd-126">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="384dd-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="384dd-127">See Also</span></span>

[<span data-ttu-id="384dd-128">GroupBy 之 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="384dd-128">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="384dd-129">GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="384dd-129">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="384dd-130">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="384dd-130">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="384dd-131">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="384dd-131">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="384dd-132">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="384dd-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
