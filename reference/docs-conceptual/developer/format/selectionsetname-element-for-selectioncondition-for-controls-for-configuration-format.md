---
title: 設定之控制項的 SelectionCondition 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368277"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="30cb9-102">設定之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="30cb9-102">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="30cb9-103">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="30cb9-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="30cb9-104">當此集合中的任何類型都存在時，就會符合條件，並使用此控制項來顯示該物件。</span><span class="sxs-lookup"><span data-stu-id="30cb9-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="30cb9-105">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="30cb9-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="30cb9-106">Configuration 元素（格式）控制項的設定（格式）控制項元素的元素，用於控制項的設定（format） CustomControl 元素，用於控制項的 CustomControl 的設定（格式） CustomEntries 元素CustomControl for 控制項的設定（格式） CustomEntry 元素，用於 CustomEntry 的設定（格式） SelectionCondition 元素的之 entryselectedby 元素適用于設定之控制項的 SelectionCondition 設定（格式） SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="30cb9-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="30cb9-107">語法</span><span class="sxs-lookup"><span data-stu-id="30cb9-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="30cb9-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="30cb9-108">Attributes and Elements</span></span>

<span data-ttu-id="30cb9-109">下列各節說明屬性、子專案，以及 `SelectionSetName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="30cb9-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="30cb9-110">屬性</span><span class="sxs-lookup"><span data-stu-id="30cb9-110">Attributes</span></span>

<span data-ttu-id="30cb9-111">無。</span><span class="sxs-lookup"><span data-stu-id="30cb9-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="30cb9-112">子元素</span><span class="sxs-lookup"><span data-stu-id="30cb9-112">Child Elements</span></span>

<span data-ttu-id="30cb9-113">無。</span><span class="sxs-lookup"><span data-stu-id="30cb9-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="30cb9-114">父元素</span><span class="sxs-lookup"><span data-stu-id="30cb9-114">Parent Elements</span></span>

|<span data-ttu-id="30cb9-115">元素</span><span class="sxs-lookup"><span data-stu-id="30cb9-115">Element</span></span>|<span data-ttu-id="30cb9-116">描述</span><span class="sxs-lookup"><span data-stu-id="30cb9-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="30cb9-117">設定之控制項的之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="30cb9-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="30cb9-118">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="30cb9-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="30cb9-119">文字值</span><span class="sxs-lookup"><span data-stu-id="30cb9-119">Text Value</span></span>

<span data-ttu-id="30cb9-120">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="30cb9-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="30cb9-121">備註</span><span class="sxs-lookup"><span data-stu-id="30cb9-121">Remarks</span></span>

<span data-ttu-id="30cb9-122">選取範圍是一組通用的 .NET 物件，可供格式設定檔案定義的任何視圖使用。</span><span class="sxs-lookup"><span data-stu-id="30cb9-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="30cb9-123">如需建立和參考選取集的詳細資訊，請參閱[定義物件集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="30cb9-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="30cb9-124">選取條件可以指定選擇集或 .NET 類型，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="30cb9-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="30cb9-125">如需如何使用選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="30cb9-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="30cb9-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30cb9-126">See Also</span></span>

[<span data-ttu-id="30cb9-127">設定之控制項的之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="30cb9-127">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="30cb9-128">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="30cb9-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="30cb9-129">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="30cb9-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="30cb9-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="30cb9-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
