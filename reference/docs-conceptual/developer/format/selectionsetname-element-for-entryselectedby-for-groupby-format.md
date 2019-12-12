---
title: GroupBy 之之 entryselectedby 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364737"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="688a4-102">GroupBy 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="688a4-102">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="688a4-103">為清單專案指定一組 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="688a4-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="688a4-104">可以為專案指定的選擇集數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="688a4-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="688a4-105">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="688a4-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="688a4-106">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（format） CustomEntries 專案的 groupby （format） CustomControl 元素，適用于的 CustomControl for GroupBy （format） CustomEntry 元素適用于 CustomEntry for groupby （format） SelectionSetName 元素的 GroupBy （format）之 entryselectedby 元素的 CustomControl</span><span class="sxs-lookup"><span data-stu-id="688a4-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="688a4-107">語法</span><span class="sxs-lookup"><span data-stu-id="688a4-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="688a4-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="688a4-108">Attributes and Elements</span></span>

<span data-ttu-id="688a4-109">下列各節說明屬性、子專案，以及 `SelectionSetName` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="688a4-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="688a4-110">屬性</span><span class="sxs-lookup"><span data-stu-id="688a4-110">Attributes</span></span>

<span data-ttu-id="688a4-111">無。</span><span class="sxs-lookup"><span data-stu-id="688a4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="688a4-112">子元素</span><span class="sxs-lookup"><span data-stu-id="688a4-112">Child Elements</span></span>

<span data-ttu-id="688a4-113">無。</span><span class="sxs-lookup"><span data-stu-id="688a4-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="688a4-114">父元素</span><span class="sxs-lookup"><span data-stu-id="688a4-114">Parent Elements</span></span>

|<span data-ttu-id="688a4-115">元素</span><span class="sxs-lookup"><span data-stu-id="688a4-115">Element</span></span>|<span data-ttu-id="688a4-116">描述</span><span class="sxs-lookup"><span data-stu-id="688a4-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="688a4-117">GroupBy 之 CustomEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="688a4-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="688a4-118">定義使用此自訂專案的 .NET 類型，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="688a4-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="688a4-119">文字值</span><span class="sxs-lookup"><span data-stu-id="688a4-119">Text Value</span></span>

<span data-ttu-id="688a4-120">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="688a4-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="688a4-121">備註</span><span class="sxs-lookup"><span data-stu-id="688a4-121">Remarks</span></span>

<span data-ttu-id="688a4-122">每個自訂控制項定義都必須定義至少一個型別名稱、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="688a4-122">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="688a4-123">當您想要定義多個視圖中使用的一組物件時，通常會使用選取範圍集。</span><span class="sxs-lookup"><span data-stu-id="688a4-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="688a4-124">例如，您可能會想要建立一組相同物件的資料表視圖和清單視圖。</span><span class="sxs-lookup"><span data-stu-id="688a4-124">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="688a4-125">如需定義選取集的詳細資訊，請參閱[定義選取範圍集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="688a4-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="688a4-126">如需自訂控制項視圖之元件的詳細資訊，請參閱[建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="688a4-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="688a4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="688a4-127">See Also</span></span>

[<span data-ttu-id="688a4-128">GroupBy 之 CustomEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="688a4-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="688a4-129">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="688a4-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="688a4-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="688a4-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
