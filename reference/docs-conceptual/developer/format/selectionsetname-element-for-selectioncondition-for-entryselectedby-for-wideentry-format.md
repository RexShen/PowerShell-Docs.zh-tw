---
title: WideEntry 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a13a429c-a31b-4e29-828c-c0c0917b5415
caps.latest.revision: 11
ms.openlocfilehash: baea89e4b259611dfa45b6bcf94fa0bf2df6b9de
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368407"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="c9724-102">WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c9724-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="c9724-103">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="c9724-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="c9724-104">當此集合中的任何類型都存在時，就會符合條件，並使用此寬視圖的定義來顯示該物件。</span><span class="sxs-lookup"><span data-stu-id="c9724-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="c9724-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（格式）之 entryselectedby 元素（代表的 WideEntry （格式） SelectionCondition 元素）之 entryselectedby for WideEntry （Format） SelectionSetName 元素，用於之 entryselectedby for WideEntry 的 SelectionCondition （格式）</span><span class="sxs-lookup"><span data-stu-id="c9724-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c9724-106">語法</span><span class="sxs-lookup"><span data-stu-id="c9724-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c9724-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="c9724-107">Attributes and Elements</span></span>

<span data-ttu-id="c9724-108">下列各節說明屬性、子專案，以及 `SelectionSetName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="c9724-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c9724-109">屬性</span><span class="sxs-lookup"><span data-stu-id="c9724-109">Attributes</span></span>

<span data-ttu-id="c9724-110">無。</span><span class="sxs-lookup"><span data-stu-id="c9724-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c9724-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c9724-111">Child Elements</span></span>

<span data-ttu-id="c9724-112">無。</span><span class="sxs-lookup"><span data-stu-id="c9724-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c9724-113">父元素</span><span class="sxs-lookup"><span data-stu-id="c9724-113">Parent Elements</span></span>

|<span data-ttu-id="c9724-114">元素</span><span class="sxs-lookup"><span data-stu-id="c9724-114">Element</span></span>|<span data-ttu-id="c9724-115">描述</span><span class="sxs-lookup"><span data-stu-id="c9724-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c9724-116">WideEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c9724-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="c9724-117">定義必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="c9724-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c9724-118">文字值</span><span class="sxs-lookup"><span data-stu-id="c9724-118">Text Value</span></span>

<span data-ttu-id="c9724-119">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="c9724-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="c9724-120">備註</span><span class="sxs-lookup"><span data-stu-id="c9724-120">Remarks</span></span>

<span data-ttu-id="c9724-121">選取條件可以指定選擇集或 .NET 類型，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="c9724-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="c9724-122">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c9724-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="c9724-123">選取範圍是一組通用的 .NET 物件，可供格式設定檔案定義的任何視圖使用。</span><span class="sxs-lookup"><span data-stu-id="c9724-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="c9724-124">如需建立和參考選取集的詳細資訊，請參閱[定義物件集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="c9724-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="c9724-125">如需有關寬視圖之其他元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="c9724-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c9724-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9724-126">See Also</span></span>

[<span data-ttu-id="c9724-127">建立寬型視圖</span><span class="sxs-lookup"><span data-stu-id="c9724-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="c9724-128">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="c9724-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c9724-129">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="c9724-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="c9724-130">WideEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c9724-130">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="c9724-131">WideEntry 之之 entryselectedby 的 SelectionCondition 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c9724-131">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="c9724-132">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="c9724-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
