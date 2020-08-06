---
title: CustomControl for View (格式) 的 SelectionCondition 的 SelectionSetName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c7fdd92475ba24d27e61371d1c6b54fa1a55647c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787507"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="aeeaa-102">檢視之 CustomControl 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="aeeaa-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="aeeaa-103">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="aeeaa-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="aeeaa-104">當此集合中的任何類型都存在時，就會符合條件，並使用此控制項來顯示該物件。</span><span class="sxs-lookup"><span data-stu-id="aeeaa-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="aeeaa-105">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="aeeaa-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="aeeaa-106">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 專案 (格式) CustomControl for view (CustomEntry 元素（CustomEntries for view) 之 entryselectedby 元素的 CustomEntry for view (格式) </span><span class="sxs-lookup"><span data-stu-id="aeeaa-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aeeaa-107">語法</span><span class="sxs-lookup"><span data-stu-id="aeeaa-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aeeaa-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="aeeaa-108">Attributes and Elements</span></span>

<span data-ttu-id="aeeaa-109">下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="aeeaa-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aeeaa-110">屬性</span><span class="sxs-lookup"><span data-stu-id="aeeaa-110">Attributes</span></span>

<span data-ttu-id="aeeaa-111">無。</span><span class="sxs-lookup"><span data-stu-id="aeeaa-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aeeaa-112">子元素</span><span class="sxs-lookup"><span data-stu-id="aeeaa-112">Child Elements</span></span>

<span data-ttu-id="aeeaa-113">無。</span><span class="sxs-lookup"><span data-stu-id="aeeaa-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="aeeaa-114">父項目</span><span class="sxs-lookup"><span data-stu-id="aeeaa-114">Parent Elements</span></span>

|<span data-ttu-id="aeeaa-115">元素</span><span class="sxs-lookup"><span data-stu-id="aeeaa-115">Element</span></span>|<span data-ttu-id="aeeaa-116">描述</span><span class="sxs-lookup"><span data-stu-id="aeeaa-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aeeaa-117">CustomControl for View (格式) 的之 entryselectedby 的 SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="aeeaa-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="aeeaa-118">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="aeeaa-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="aeeaa-119">文字值</span><span class="sxs-lookup"><span data-stu-id="aeeaa-119">Text Value</span></span>

<span data-ttu-id="aeeaa-120">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="aeeaa-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="aeeaa-121">備註</span><span class="sxs-lookup"><span data-stu-id="aeeaa-121">Remarks</span></span>

<span data-ttu-id="aeeaa-122">選取範圍是一組通用的 .NET 物件，可供格式設定檔案定義的任何視圖使用。</span><span class="sxs-lookup"><span data-stu-id="aeeaa-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="aeeaa-123">如需建立和參考選取集的詳細資訊，請參閱[定義物件集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="aeeaa-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="aeeaa-124">選取條件可以指定選擇集或 .NET 類型，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="aeeaa-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="aeeaa-125">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="aeeaa-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aeeaa-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aeeaa-126">See Also</span></span>

[<span data-ttu-id="aeeaa-127">CustomControl for View (格式) 的之 entryselectedby 的 SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="aeeaa-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="aeeaa-128">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="aeeaa-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="aeeaa-129">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="aeeaa-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="aeeaa-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="aeeaa-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
