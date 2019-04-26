---
title: SelectionSetName SelectionCondition 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064007"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="a5dc8-102">設定之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a5dc8-102">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="a5dc8-103">指定的觸發條件的.NET 型別集。</span><span class="sxs-lookup"><span data-stu-id="a5dc8-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="a5dc8-104">當有任何在這組型別時，符合條件，並使用這個控制項顯示物件。</span><span class="sxs-lookup"><span data-stu-id="a5dc8-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="a5dc8-105">定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="a5dc8-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="a5dc8-106">組態 （格式） 的組態 （格式） CustomControl 項目控制項的 CustomControl 的組態 （格式） CustomEntries 項目控制項的控制項的控制項項目的組態項目 （格式） 的控制項項目控制項的 EntrySelectedBy 的組態 （格式） SelectionCondition 項目控制項的 CustomEntry 的組態 （格式） EntrySelectedBy 項目控制項的 CustomControl 的組態 （格式） CustomEntry 項目SelectionCondition 控制項組態 （格式） 的組態 （格式） SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="a5dc8-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a5dc8-107">語法</span><span class="sxs-lookup"><span data-stu-id="a5dc8-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a5dc8-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a5dc8-108">Attributes and Elements</span></span>

<span data-ttu-id="a5dc8-109">下列各節說明屬性、 子項目和父項目`SelectionSetName`項目。</span><span class="sxs-lookup"><span data-stu-id="a5dc8-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a5dc8-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a5dc8-110">Attributes</span></span>

<span data-ttu-id="a5dc8-111">無。</span><span class="sxs-lookup"><span data-stu-id="a5dc8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a5dc8-112">子元素</span><span class="sxs-lookup"><span data-stu-id="a5dc8-112">Child Elements</span></span>

<span data-ttu-id="a5dc8-113">無。</span><span class="sxs-lookup"><span data-stu-id="a5dc8-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a5dc8-114">父項目</span><span class="sxs-lookup"><span data-stu-id="a5dc8-114">Parent Elements</span></span>

|<span data-ttu-id="a5dc8-115">項目</span><span class="sxs-lookup"><span data-stu-id="a5dc8-115">Element</span></span>|<span data-ttu-id="a5dc8-116">描述</span><span class="sxs-lookup"><span data-stu-id="a5dc8-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a5dc8-117">SelectionCondition EntrySelectedBy 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="a5dc8-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="a5dc8-118">定義必須存在，要使用的控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="a5dc8-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a5dc8-119">文字值</span><span class="sxs-lookup"><span data-stu-id="a5dc8-119">Text Value</span></span>

<span data-ttu-id="a5dc8-120">指定選取項目集的名稱。</span><span class="sxs-lookup"><span data-stu-id="a5dc8-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="a5dc8-121">備註</span><span class="sxs-lookup"><span data-stu-id="a5dc8-121">Remarks</span></span>

<span data-ttu-id="a5dc8-122">選取項目集是常見的.NET 物件，可供任何檢視中定義的格式化檔案群組。</span><span class="sxs-lookup"><span data-stu-id="a5dc8-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="a5dc8-123">如需有關建立及參考選取項目集的詳細資訊，請參閱 <<c0> [ 定義設定的物件](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="a5dc8-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="a5dc8-124">選取條件可以指定的選取項目集或.NET 類型，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="a5dc8-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="a5dc8-125">如需如何使用選擇條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a5dc8-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a5dc8-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5dc8-126">See Also</span></span>

[<span data-ttu-id="a5dc8-127">SelectionCondition EntrySelectedBy 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="a5dc8-127">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="a5dc8-128">定義何時顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="a5dc8-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a5dc8-129">定義選取範圍</span><span class="sxs-lookup"><span data-stu-id="a5dc8-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="a5dc8-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="a5dc8-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
