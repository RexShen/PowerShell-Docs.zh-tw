---
title: ListEntry 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368397"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="114be-102">ListEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="114be-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="114be-103">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="114be-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="114be-104">當此集合中的任何類型都存在時，就會符合條件，並使用此清單視圖的定義來顯示該物件。</span><span class="sxs-lookup"><span data-stu-id="114be-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="114be-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（格式） ListEntries 元素（格式） ListEntry 元素（格式）之 entryselectedby 元素（代表的 ListEntry （格式） SelectionCondition 元素）之 entryselectedby for ListEntry （Format） SelectionSetName 元素，用於之 entryselectedby for ListEntry 的 SelectionCondition （格式）</span><span class="sxs-lookup"><span data-stu-id="114be-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="114be-106">語法</span><span class="sxs-lookup"><span data-stu-id="114be-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="114be-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="114be-107">Attributes and Elements</span></span>

<span data-ttu-id="114be-108">下列各節說明屬性、子專案，以及 `SelectionSetName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="114be-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="114be-109">屬性</span><span class="sxs-lookup"><span data-stu-id="114be-109">Attributes</span></span>

<span data-ttu-id="114be-110">無。</span><span class="sxs-lookup"><span data-stu-id="114be-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="114be-111">子元素</span><span class="sxs-lookup"><span data-stu-id="114be-111">Child Elements</span></span>

<span data-ttu-id="114be-112">無。</span><span class="sxs-lookup"><span data-stu-id="114be-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="114be-113">父元素</span><span class="sxs-lookup"><span data-stu-id="114be-113">Parent Elements</span></span>

|<span data-ttu-id="114be-114">元素</span><span class="sxs-lookup"><span data-stu-id="114be-114">Element</span></span>|<span data-ttu-id="114be-115">描述</span><span class="sxs-lookup"><span data-stu-id="114be-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="114be-116">ListEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="114be-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="114be-117">定義必須存在才能使用此清單視圖定義的條件。</span><span class="sxs-lookup"><span data-stu-id="114be-117">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="114be-118">文字值</span><span class="sxs-lookup"><span data-stu-id="114be-118">Text Value</span></span>

<span data-ttu-id="114be-119">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="114be-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="114be-120">備註</span><span class="sxs-lookup"><span data-stu-id="114be-120">Remarks</span></span>

<span data-ttu-id="114be-121">選取條件可以指定選擇集或 .NET 類型，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="114be-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="114be-122">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="114be-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="114be-123">選取範圍是一組通用的 .NET 物件，可供格式設定檔案定義的任何視圖使用。</span><span class="sxs-lookup"><span data-stu-id="114be-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="114be-124">如需建立和參考選取集的詳細資訊，請參閱[定義物件集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="114be-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="114be-125">如需清單視圖之其他元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="114be-125">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="114be-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="114be-126">See Also</span></span>

[<span data-ttu-id="114be-127">建立清單視圖</span><span class="sxs-lookup"><span data-stu-id="114be-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="114be-128">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="114be-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="114be-129">ListEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="114be-129">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="114be-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="114be-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
