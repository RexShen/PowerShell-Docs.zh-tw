---
title: TableControl 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361917"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="04082-102">TableControl 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="04082-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="04082-103">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="04082-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="04082-104">當此集合中的任何類型都存在時，就會符合條件，並使用資料表視圖的這個定義來顯示該物件。</span><span class="sxs-lookup"><span data-stu-id="04082-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="04082-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（格式）之 entryselectedby 元素（格式）SelectionCondition for 之 entryselectedby 的 TableRowEntry （Format） SelectionSetName 元素之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="04082-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="04082-106">語法</span><span class="sxs-lookup"><span data-stu-id="04082-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="04082-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="04082-107">Attributes and Elements</span></span>

<span data-ttu-id="04082-108">下列各節說明屬性、子專案，以及 `SelectionSetName` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="04082-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="04082-109">屬性</span><span class="sxs-lookup"><span data-stu-id="04082-109">Attributes</span></span>

<span data-ttu-id="04082-110">無。</span><span class="sxs-lookup"><span data-stu-id="04082-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="04082-111">子元素</span><span class="sxs-lookup"><span data-stu-id="04082-111">Child Elements</span></span>

<span data-ttu-id="04082-112">無。</span><span class="sxs-lookup"><span data-stu-id="04082-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="04082-113">父元素</span><span class="sxs-lookup"><span data-stu-id="04082-113">Parent Elements</span></span>

|<span data-ttu-id="04082-114">元素</span><span class="sxs-lookup"><span data-stu-id="04082-114">Element</span></span>|<span data-ttu-id="04082-115">描述</span><span class="sxs-lookup"><span data-stu-id="04082-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="04082-116">TableRowEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="04082-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="04082-117">定義必須存在的條件，才能用於這個資料表視圖定義。</span><span class="sxs-lookup"><span data-stu-id="04082-117">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="04082-118">文字值</span><span class="sxs-lookup"><span data-stu-id="04082-118">Text Value</span></span>

<span data-ttu-id="04082-119">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="04082-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="04082-120">備註</span><span class="sxs-lookup"><span data-stu-id="04082-120">Remarks</span></span>

<span data-ttu-id="04082-121">選取條件可以指定選擇集或 .NET 類型，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="04082-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="04082-122">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="04082-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="04082-123">選取範圍是一組通用的 .NET 物件，可供格式設定檔案定義的任何視圖使用。</span><span class="sxs-lookup"><span data-stu-id="04082-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="04082-124">如需建立和參考選取集的詳細資訊，請參閱[定義物件集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="04082-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="04082-125">如需有關寬視圖之其他元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="04082-125">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="04082-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04082-126">See Also</span></span>

[<span data-ttu-id="04082-127">建立資料表視圖</span><span class="sxs-lookup"><span data-stu-id="04082-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="04082-128">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="04082-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="04082-129">TableRowEntry 之之 entryselectedby 的 SelectionCondition 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="04082-129">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="04082-130">TableRowEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="04082-130">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="04082-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="04082-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
