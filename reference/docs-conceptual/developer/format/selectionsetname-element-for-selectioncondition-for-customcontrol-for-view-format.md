---
title: CustomControl for View 的 SelectionCondition 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368267"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="e656c-102">檢視之 CustomControl 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e656c-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="e656c-103">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="e656c-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="e656c-104">當此集合中的任何類型都存在時，就會符合條件，並使用此控制項來顯示該物件。</span><span class="sxs-lookup"><span data-stu-id="e656c-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="e656c-105">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="e656c-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="e656c-106">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素（format） CustomEntries 元素，適用于 CustomEntry for View 的 CustomControl for View （format） CustomEntries 元素（格式）之 entryselectedbyView 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e656c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e656c-107">語法</span><span class="sxs-lookup"><span data-stu-id="e656c-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e656c-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="e656c-108">Attributes and Elements</span></span>

<span data-ttu-id="e656c-109">下列各節說明屬性、子專案，以及 `SelectionSetName` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="e656c-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e656c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e656c-110">Attributes</span></span>

<span data-ttu-id="e656c-111">無。</span><span class="sxs-lookup"><span data-stu-id="e656c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e656c-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e656c-112">Child Elements</span></span>

<span data-ttu-id="e656c-113">無。</span><span class="sxs-lookup"><span data-stu-id="e656c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e656c-114">父元素</span><span class="sxs-lookup"><span data-stu-id="e656c-114">Parent Elements</span></span>

|<span data-ttu-id="e656c-115">元素</span><span class="sxs-lookup"><span data-stu-id="e656c-115">Element</span></span>|<span data-ttu-id="e656c-116">描述</span><span class="sxs-lookup"><span data-stu-id="e656c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e656c-117">CustomControl for View 的之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e656c-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="e656c-118">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="e656c-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e656c-119">文字值</span><span class="sxs-lookup"><span data-stu-id="e656c-119">Text Value</span></span>

<span data-ttu-id="e656c-120">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="e656c-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="e656c-121">備註</span><span class="sxs-lookup"><span data-stu-id="e656c-121">Remarks</span></span>

<span data-ttu-id="e656c-122">選取範圍是一組通用的 .NET 物件，可供格式設定檔案定義的任何視圖使用。</span><span class="sxs-lookup"><span data-stu-id="e656c-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="e656c-123">如需建立和參考選取集的詳細資訊，請參閱[定義物件集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="e656c-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="e656c-124">選取條件可以指定選擇集或 .NET 類型，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="e656c-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="e656c-125">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e656c-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e656c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e656c-126">See Also</span></span>

[<span data-ttu-id="e656c-127">CustomControl for View 的之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e656c-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="e656c-128">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="e656c-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e656c-129">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="e656c-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="e656c-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="e656c-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
