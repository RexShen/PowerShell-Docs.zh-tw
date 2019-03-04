---
title: 用於檢視 （格式） 的控制項 SelectionCondition SelectionSetName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855114"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="4ee89-102">檢視之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4ee89-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="4ee89-103">指定的觸發條件的.NET 型別集。</span><span class="sxs-lookup"><span data-stu-id="4ee89-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="4ee89-104">當有任何在這組型別時，即符合此條件，並使用這個控制項來顯示物件。</span><span class="sxs-lookup"><span data-stu-id="4ee89-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="4ee89-105">定義可供檢視的控制項時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="4ee89-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="4ee89-106">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目CustomControl CustomEntries CustomEntry EntrySelectedBy 的檢視 （控制項的檢視 （格式） SelectionCondition 元素的控制項的檢視 （格式） EntrySelectedBy 元素的控制項的檢視 （格式） CustomEntry 元素的控制項用於檢視 （格式） 的控制項 SelectionCondition 的格式） SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="4ee89-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4ee89-107">語法</span><span class="sxs-lookup"><span data-stu-id="4ee89-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4ee89-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="4ee89-108">Attributes and Elements</span></span>

<span data-ttu-id="4ee89-109">下列各節說明屬性、 子項目和父項目`SelectionSetName`項目。</span><span class="sxs-lookup"><span data-stu-id="4ee89-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4ee89-110">屬性</span><span class="sxs-lookup"><span data-stu-id="4ee89-110">Attributes</span></span>

<span data-ttu-id="4ee89-111">無。</span><span class="sxs-lookup"><span data-stu-id="4ee89-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4ee89-112">子元素</span><span class="sxs-lookup"><span data-stu-id="4ee89-112">Child Elements</span></span>

<span data-ttu-id="4ee89-113">無。</span><span class="sxs-lookup"><span data-stu-id="4ee89-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4ee89-114">父元素</span><span class="sxs-lookup"><span data-stu-id="4ee89-114">Parent Elements</span></span>

|<span data-ttu-id="4ee89-115">元素</span><span class="sxs-lookup"><span data-stu-id="4ee89-115">Element</span></span>|<span data-ttu-id="4ee89-116">描述</span><span class="sxs-lookup"><span data-stu-id="4ee89-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4ee89-117">用於檢視 （格式） 的控制項 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="4ee89-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="4ee89-118">定義必須存在，要使用的控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="4ee89-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4ee89-119">文字值</span><span class="sxs-lookup"><span data-stu-id="4ee89-119">Text Value</span></span>

<span data-ttu-id="4ee89-120">指定選取項目集的名稱。</span><span class="sxs-lookup"><span data-stu-id="4ee89-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="4ee89-121">備註</span><span class="sxs-lookup"><span data-stu-id="4ee89-121">Remarks</span></span>

<span data-ttu-id="4ee89-122">選取項目集是常見的.NET 物件，可供任何檢視中定義的格式化檔案群組。</span><span class="sxs-lookup"><span data-stu-id="4ee89-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="4ee89-123">如需有關建立及參考選取項目集的詳細資訊，請參閱 <<c0> [ 定義的選取項目設定](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="4ee89-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="4ee89-124">選取條件可以指定的選取項目集或.NET 類型，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="4ee89-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="4ee89-125">如需如何使用選擇條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="4ee89-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4ee89-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ee89-126">See Also</span></span>

[<span data-ttu-id="4ee89-127">用於檢視 （格式） 的控制項 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="4ee89-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="4ee89-128">定義何時顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="4ee89-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="4ee89-129">定義選取範圍</span><span class="sxs-lookup"><span data-stu-id="4ee89-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="4ee89-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="4ee89-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
