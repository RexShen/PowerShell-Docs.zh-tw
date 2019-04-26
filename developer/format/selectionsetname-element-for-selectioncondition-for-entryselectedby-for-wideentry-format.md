---
title: 針對 WideEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a13a429c-a31b-4e29-828c-c0c0917b5415
caps.latest.revision: 11
ms.openlocfilehash: baea89e4b259611dfa45b6bcf94fa0bf2df6b9de
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075472"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="7583e-102">WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7583e-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="7583e-103">指定的觸發條件的.NET 型別集。</span><span class="sxs-lookup"><span data-stu-id="7583e-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="7583e-104">當有任何在這組型別時，符合條件，並使用此定義的寬型檢視來顯示物件。</span><span class="sxs-lookup"><span data-stu-id="7583e-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="7583e-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry 項目 （格式） EntrySelectedBy 項目用於 WideEntry （格式） SelectionCondition 元素EntrySelectedBy WideEntry （格式） 的 EntrySelectedBy 的 SelectionCondition WideEntry （格式） SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="7583e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7583e-106">語法</span><span class="sxs-lookup"><span data-stu-id="7583e-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7583e-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7583e-107">Attributes and Elements</span></span>

<span data-ttu-id="7583e-108">下列各節說明屬性、 子項目和父項目`SelectionSetName`項目。</span><span class="sxs-lookup"><span data-stu-id="7583e-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7583e-109">屬性</span><span class="sxs-lookup"><span data-stu-id="7583e-109">Attributes</span></span>

<span data-ttu-id="7583e-110">無。</span><span class="sxs-lookup"><span data-stu-id="7583e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7583e-111">子元素</span><span class="sxs-lookup"><span data-stu-id="7583e-111">Child Elements</span></span>

<span data-ttu-id="7583e-112">無。</span><span class="sxs-lookup"><span data-stu-id="7583e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7583e-113">父項目</span><span class="sxs-lookup"><span data-stu-id="7583e-113">Parent Elements</span></span>

|<span data-ttu-id="7583e-114">項目</span><span class="sxs-lookup"><span data-stu-id="7583e-114">Element</span></span>|<span data-ttu-id="7583e-115">描述</span><span class="sxs-lookup"><span data-stu-id="7583e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7583e-116">WideEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="7583e-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="7583e-117">定義要使用此定義必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="7583e-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7583e-118">文字值</span><span class="sxs-lookup"><span data-stu-id="7583e-118">Text Value</span></span>

<span data-ttu-id="7583e-119">指定選取項目集的名稱。</span><span class="sxs-lookup"><span data-stu-id="7583e-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="7583e-120">備註</span><span class="sxs-lookup"><span data-stu-id="7583e-120">Remarks</span></span>

<span data-ttu-id="7583e-121">選取條件可以指定的選取項目集或.NET 類型，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="7583e-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="7583e-122">如需如何使用選擇條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7583e-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="7583e-123">選取項目集是常見的.NET 物件，可供任何檢視中定義的格式化檔案群組。</span><span class="sxs-lookup"><span data-stu-id="7583e-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="7583e-124">如需有關建立及參考選取項目集的詳細資訊，請參閱 <<c0> [ 定義設定的物件](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="7583e-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="7583e-125">寬型檢視的其他元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="7583e-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7583e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7583e-126">See Also</span></span>

[<span data-ttu-id="7583e-127">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="7583e-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="7583e-128">定義何時顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="7583e-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7583e-129">定義選取範圍</span><span class="sxs-lookup"><span data-stu-id="7583e-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="7583e-130">WideEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="7583e-130">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="7583e-131">針對 WideEntry （格式） 的 EntrySelectedBy SelectionCondition TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="7583e-131">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="7583e-132">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="7583e-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
