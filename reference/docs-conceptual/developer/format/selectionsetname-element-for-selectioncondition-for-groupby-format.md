---
title: GroupBy 之 SelectionCondition 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361857"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="21495-102">GroupBy 之 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="21495-102">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="21495-103">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="21495-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="21495-104">當此集合中的任何類型都存在時，就會符合條件，並使用此控制項來顯示該物件。</span><span class="sxs-lookup"><span data-stu-id="21495-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="21495-105">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="21495-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="21495-106">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（format） CustomEntries 專案的 groupby （format） CustomControl 元素，適用于的 CustomControl for GroupBy （format） CustomEntry 元素適用于之 entryselectedby for groupby （format） SelectionSetName 元素的 groupby （format） SelectionCondition 元素的 GroupBy （格式）之 entryselectedby 元素的 CustomControl</span><span class="sxs-lookup"><span data-stu-id="21495-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="21495-107">語法</span><span class="sxs-lookup"><span data-stu-id="21495-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="21495-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="21495-108">Attributes and Elements</span></span>

<span data-ttu-id="21495-109">下列各節說明屬性、子專案，以及 `SelectionSetName` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="21495-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="21495-110">屬性</span><span class="sxs-lookup"><span data-stu-id="21495-110">Attributes</span></span>

<span data-ttu-id="21495-111">無。</span><span class="sxs-lookup"><span data-stu-id="21495-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="21495-112">子元素</span><span class="sxs-lookup"><span data-stu-id="21495-112">Child Elements</span></span>

<span data-ttu-id="21495-113">無。</span><span class="sxs-lookup"><span data-stu-id="21495-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="21495-114">父元素</span><span class="sxs-lookup"><span data-stu-id="21495-114">Parent Elements</span></span>

|<span data-ttu-id="21495-115">元素</span><span class="sxs-lookup"><span data-stu-id="21495-115">Element</span></span>|<span data-ttu-id="21495-116">描述</span><span class="sxs-lookup"><span data-stu-id="21495-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="21495-117">GroupBy 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21495-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="21495-118">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="21495-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="21495-119">文字值</span><span class="sxs-lookup"><span data-stu-id="21495-119">Text Value</span></span>

<span data-ttu-id="21495-120">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="21495-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="21495-121">備註</span><span class="sxs-lookup"><span data-stu-id="21495-121">Remarks</span></span>

<span data-ttu-id="21495-122">選取範圍是一組通用的 .NET 物件，可供格式設定檔案定義的任何視圖使用。</span><span class="sxs-lookup"><span data-stu-id="21495-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="21495-123">如需建立和參考選取集的詳細資訊，請參閱[定義選取範圍](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="21495-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="21495-124">當指定此元素時，您無法指定[TypeName](./typename-element-for-selectioncondition-for-groupby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="21495-124">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="21495-125">如需定義選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="21495-125">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="21495-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21495-126">See Also</span></span>

[<span data-ttu-id="21495-127">GroupBy 之 SelectionCondition 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21495-127">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="21495-128">GroupBy 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21495-128">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="21495-129">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="21495-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="21495-130">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="21495-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="21495-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="21495-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
