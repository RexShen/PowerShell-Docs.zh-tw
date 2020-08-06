---
title: View (Format) 的控制項之 SelectionCondition 的 SelectionSetName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0feb23f860487952344680f75ee674e9e0e6dcc6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787524"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="e1043-102">檢視之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e1043-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="e1043-103">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="e1043-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="e1043-104">當此集合中的任何類型都存在時，就會符合條件，並使用此控制項來顯示該物件。</span><span class="sxs-lookup"><span data-stu-id="e1043-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="e1043-105">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="e1043-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e1043-106">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 CustomControl 格式 (CustomEntries 元素用於 view 的控制項)  ( (格式) 的控制項適用于 CustomEntries 的 CustomEntry 元素，用於 view (Format) 之 entryselectedby 專案 CustomEntry for view (format) SelectionCondition 元素 for view (format) 之 entryselectedby 專案 for SelectionSetName for Controls 的控制項</span><span class="sxs-lookup"><span data-stu-id="e1043-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e1043-107">語法</span><span class="sxs-lookup"><span data-stu-id="e1043-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e1043-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e1043-108">Attributes and Elements</span></span>

<span data-ttu-id="e1043-109">下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="e1043-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e1043-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e1043-110">Attributes</span></span>

<span data-ttu-id="e1043-111">無。</span><span class="sxs-lookup"><span data-stu-id="e1043-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e1043-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e1043-112">Child Elements</span></span>

<span data-ttu-id="e1043-113">無。</span><span class="sxs-lookup"><span data-stu-id="e1043-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e1043-114">父項目</span><span class="sxs-lookup"><span data-stu-id="e1043-114">Parent Elements</span></span>

|<span data-ttu-id="e1043-115">元素</span><span class="sxs-lookup"><span data-stu-id="e1043-115">Element</span></span>|<span data-ttu-id="e1043-116">描述</span><span class="sxs-lookup"><span data-stu-id="e1043-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1043-117">檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e1043-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="e1043-118">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="e1043-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e1043-119">文字值</span><span class="sxs-lookup"><span data-stu-id="e1043-119">Text Value</span></span>

<span data-ttu-id="e1043-120">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="e1043-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="e1043-121">備註</span><span class="sxs-lookup"><span data-stu-id="e1043-121">Remarks</span></span>

<span data-ttu-id="e1043-122">選取範圍是一組通用的 .NET 物件，可供格式設定檔案定義的任何視圖使用。</span><span class="sxs-lookup"><span data-stu-id="e1043-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="e1043-123">如需建立和參考選取集的詳細資訊，請參閱[定義選取範圍](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="e1043-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="e1043-124">選取條件可以指定選擇集或 .NET 類型，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="e1043-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="e1043-125">如需如何使用選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e1043-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e1043-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1043-126">See Also</span></span>

[<span data-ttu-id="e1043-127">檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e1043-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="e1043-128">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="e1043-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e1043-129">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="e1043-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="e1043-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="e1043-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
