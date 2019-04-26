---
title: TableControl （格式） 的 EntrySelectedBy 的 SelectionCondition SelectionSetName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064045"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="cad7e-102">TableControl 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="cad7e-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="cad7e-103">指定的觸發條件的.NET 型別集。</span><span class="sxs-lookup"><span data-stu-id="cad7e-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="cad7e-104">當有任何在這組型別時，符合條件，並使用此定義的資料表檢視中顯示物件。</span><span class="sxs-lookup"><span data-stu-id="cad7e-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="cad7e-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 （格式） TableRowEntry 項目 （格式） EntrySelectedBy 項目 TableRowEntry （格式）SelectionCondition EntrySelectedBy TableRowEntry （格式） 的 EntrySelectedBy 的 SelectionCondition TableRowEntry （格式） SelectionSetName 元素的項目</span><span class="sxs-lookup"><span data-stu-id="cad7e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cad7e-106">語法</span><span class="sxs-lookup"><span data-stu-id="cad7e-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cad7e-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cad7e-107">Attributes and Elements</span></span>

<span data-ttu-id="cad7e-108">下列各節說明屬性、 子項目和父項目`SelectionSetName`項目。</span><span class="sxs-lookup"><span data-stu-id="cad7e-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cad7e-109">屬性</span><span class="sxs-lookup"><span data-stu-id="cad7e-109">Attributes</span></span>

<span data-ttu-id="cad7e-110">無。</span><span class="sxs-lookup"><span data-stu-id="cad7e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cad7e-111">子元素</span><span class="sxs-lookup"><span data-stu-id="cad7e-111">Child Elements</span></span>

<span data-ttu-id="cad7e-112">無。</span><span class="sxs-lookup"><span data-stu-id="cad7e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cad7e-113">父項目</span><span class="sxs-lookup"><span data-stu-id="cad7e-113">Parent Elements</span></span>

|<span data-ttu-id="cad7e-114">項目</span><span class="sxs-lookup"><span data-stu-id="cad7e-114">Element</span></span>|<span data-ttu-id="cad7e-115">描述</span><span class="sxs-lookup"><span data-stu-id="cad7e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cad7e-116">TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="cad7e-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="cad7e-117">定義要用於此 [資料表] 檢視的定義必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="cad7e-117">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cad7e-118">文字值</span><span class="sxs-lookup"><span data-stu-id="cad7e-118">Text Value</span></span>

<span data-ttu-id="cad7e-119">指定選取項目集的名稱。</span><span class="sxs-lookup"><span data-stu-id="cad7e-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="cad7e-120">備註</span><span class="sxs-lookup"><span data-stu-id="cad7e-120">Remarks</span></span>

<span data-ttu-id="cad7e-121">選取條件可以指定的選取項目集或.NET 類型，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="cad7e-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="cad7e-122">如需如何使用選擇條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="cad7e-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="cad7e-123">選取項目集是常見的.NET 物件，可供任何檢視中定義的格式化檔案群組。</span><span class="sxs-lookup"><span data-stu-id="cad7e-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="cad7e-124">如需有關建立及參考選取項目集的詳細資訊，請參閱 <<c0> [ 定義設定的物件](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="cad7e-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="cad7e-125">寬型檢視的其他元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="cad7e-125">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cad7e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cad7e-126">See Also</span></span>

[<span data-ttu-id="cad7e-127">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="cad7e-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="cad7e-128">定義何時顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="cad7e-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="cad7e-129">針對 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="cad7e-129">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="cad7e-130">TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="cad7e-130">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="cad7e-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="cad7e-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
