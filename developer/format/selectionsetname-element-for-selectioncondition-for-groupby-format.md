---
title: GroupBy （格式） 的 SelectionCondition SelectionSetName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856754"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="49737-102">GroupBy 之 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="49737-102">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="49737-103">指定的觸發條件的.NET 型別集。</span><span class="sxs-lookup"><span data-stu-id="49737-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="49737-104">當有任何在這組型別時，符合條件，並使用這個控制項顯示物件。</span><span class="sxs-lookup"><span data-stu-id="49737-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="49737-105">定義新的群組物件的顯示方式時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="49737-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="49737-106">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素CustomControl CustomEntry EntrySelectedBy SelectionCondition 的 GroupBy （格式） 的 GroupBy （格式） SelectionSetName 元素的 GroupBy （格式） SelectionCondition 元素的 GroupBy （格式） EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="49737-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="49737-107">語法</span><span class="sxs-lookup"><span data-stu-id="49737-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="49737-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="49737-108">Attributes and Elements</span></span>

<span data-ttu-id="49737-109">下列各節說明屬性、 子項目和父項目`SelectionSetName`項目。</span><span class="sxs-lookup"><span data-stu-id="49737-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="49737-110">屬性</span><span class="sxs-lookup"><span data-stu-id="49737-110">Attributes</span></span>

<span data-ttu-id="49737-111">無。</span><span class="sxs-lookup"><span data-stu-id="49737-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="49737-112">子元素</span><span class="sxs-lookup"><span data-stu-id="49737-112">Child Elements</span></span>

<span data-ttu-id="49737-113">無。</span><span class="sxs-lookup"><span data-stu-id="49737-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="49737-114">父元素</span><span class="sxs-lookup"><span data-stu-id="49737-114">Parent Elements</span></span>

|<span data-ttu-id="49737-115">元素</span><span class="sxs-lookup"><span data-stu-id="49737-115">Element</span></span>|<span data-ttu-id="49737-116">描述</span><span class="sxs-lookup"><span data-stu-id="49737-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="49737-117">GroupBy （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="49737-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="49737-118">定義必須存在，要使用的控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="49737-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="49737-119">文字值</span><span class="sxs-lookup"><span data-stu-id="49737-119">Text Value</span></span>

<span data-ttu-id="49737-120">指定選取項目集的名稱。</span><span class="sxs-lookup"><span data-stu-id="49737-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="49737-121">備註</span><span class="sxs-lookup"><span data-stu-id="49737-121">Remarks</span></span>

<span data-ttu-id="49737-122">選取項目集是常見的.NET 物件，可供任何檢視中定義的格式化檔案群組。</span><span class="sxs-lookup"><span data-stu-id="49737-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="49737-123">如需有關建立及參考選取項目集的詳細資訊，請參閱 <<c0> [ 定義的選取項目設定](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="49737-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="49737-124">當指定這個項目時，您無法指定[TypeName](./typename-element-for-selectioncondition-for-groupby-format.md)項目。</span><span class="sxs-lookup"><span data-stu-id="49737-124">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="49737-125">如需定義選擇條件的詳細資訊，請參閱 <<c0> [ 定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="49737-125">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="49737-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49737-126">See Also</span></span>

[<span data-ttu-id="49737-127">GroupBy （格式） 的 SelectionCondition TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="49737-127">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="49737-128">GroupBy （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="49737-128">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="49737-129">定義何時顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="49737-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="49737-130">定義選取範圍</span><span class="sxs-lookup"><span data-stu-id="49737-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="49737-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="49737-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
