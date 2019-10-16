---
title: View 之控制項的 SelectionCondition 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361967"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="bb679-102">檢視之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bb679-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="bb679-103">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="bb679-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="bb679-104">當此集合中的任何類型都存在時，就會符合條件，並使用此控制項來顯示該物件。</span><span class="sxs-lookup"><span data-stu-id="bb679-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="bb679-105">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="bb679-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="bb679-106">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素CustomControl for view （format） CustomEntry 元素的 CustomEntries for view （format）之 entryselectedby 元素 for CustomEntry for view （format） SelectionCondition 元素 for controls 的控制項（格式）Format） SelectionSetName 元素，用於 View 的控制項 SelectionCondition （格式）</span><span class="sxs-lookup"><span data-stu-id="bb679-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bb679-107">語法</span><span class="sxs-lookup"><span data-stu-id="bb679-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bb679-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="bb679-108">Attributes and Elements</span></span>

<span data-ttu-id="bb679-109">下列各節說明屬性、子專案，以及 `SelectionSetName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="bb679-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bb679-110">屬性</span><span class="sxs-lookup"><span data-stu-id="bb679-110">Attributes</span></span>

<span data-ttu-id="bb679-111">無。</span><span class="sxs-lookup"><span data-stu-id="bb679-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bb679-112">子元素</span><span class="sxs-lookup"><span data-stu-id="bb679-112">Child Elements</span></span>

<span data-ttu-id="bb679-113">無。</span><span class="sxs-lookup"><span data-stu-id="bb679-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bb679-114">父元素</span><span class="sxs-lookup"><span data-stu-id="bb679-114">Parent Elements</span></span>

|<span data-ttu-id="bb679-115">元素</span><span class="sxs-lookup"><span data-stu-id="bb679-115">Element</span></span>|<span data-ttu-id="bb679-116">描述</span><span class="sxs-lookup"><span data-stu-id="bb679-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bb679-117">View 之控制項的之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="bb679-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="bb679-118">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="bb679-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bb679-119">文字值</span><span class="sxs-lookup"><span data-stu-id="bb679-119">Text Value</span></span>

<span data-ttu-id="bb679-120">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="bb679-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="bb679-121">備註</span><span class="sxs-lookup"><span data-stu-id="bb679-121">Remarks</span></span>

<span data-ttu-id="bb679-122">選取範圍是一組通用的 .NET 物件，可供格式設定檔案定義的任何視圖使用。</span><span class="sxs-lookup"><span data-stu-id="bb679-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="bb679-123">如需建立和參考選取集的詳細資訊，請參閱[定義選取範圍](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="bb679-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="bb679-124">選取條件可以指定選擇集或 .NET 類型，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="bb679-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="bb679-125">如需如何使用選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="bb679-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bb679-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb679-126">See Also</span></span>

[<span data-ttu-id="bb679-127">View 之控制項的之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="bb679-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="bb679-128">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="bb679-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="bb679-129">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="bb679-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="bb679-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="bb679-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
