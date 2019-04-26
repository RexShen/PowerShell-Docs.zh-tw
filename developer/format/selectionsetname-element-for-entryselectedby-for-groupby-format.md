---
title: GroupBy （格式） 的 EntrySelectedBy SelectionSetName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064062"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="c14fd-102">GroupBy 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c14fd-102">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="c14fd-103">指定一組.NET 物件清單項目。</span><span class="sxs-lookup"><span data-stu-id="c14fd-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="c14fd-104">可供指定的項目選取項目集的數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="c14fd-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="c14fd-105">定義新的群組物件的顯示方式時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="c14fd-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="c14fd-106">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素CustomControl CustomEntry EntrySelectedBy 的 GroupBy （格式） 的 GroupBy （格式） SelectionSetName 元素的 GroupBy （格式） EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="c14fd-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c14fd-107">語法</span><span class="sxs-lookup"><span data-stu-id="c14fd-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c14fd-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c14fd-108">Attributes and Elements</span></span>

<span data-ttu-id="c14fd-109">下列各節說明屬性、 子項目和父項目`SelectionSetName`項目。</span><span class="sxs-lookup"><span data-stu-id="c14fd-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c14fd-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c14fd-110">Attributes</span></span>

<span data-ttu-id="c14fd-111">無。</span><span class="sxs-lookup"><span data-stu-id="c14fd-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c14fd-112">子元素</span><span class="sxs-lookup"><span data-stu-id="c14fd-112">Child Elements</span></span>

<span data-ttu-id="c14fd-113">無。</span><span class="sxs-lookup"><span data-stu-id="c14fd-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c14fd-114">父項目</span><span class="sxs-lookup"><span data-stu-id="c14fd-114">Parent Elements</span></span>

|<span data-ttu-id="c14fd-115">項目</span><span class="sxs-lookup"><span data-stu-id="c14fd-115">Element</span></span>|<span data-ttu-id="c14fd-116">描述</span><span class="sxs-lookup"><span data-stu-id="c14fd-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c14fd-117">GroupBy （格式） 的 CustomEntry EntrySelectedBy 項目</span><span class="sxs-lookup"><span data-stu-id="c14fd-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="c14fd-118">定義.NET 型別，使用此自訂的項目或要使用此項目必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="c14fd-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c14fd-119">文字值</span><span class="sxs-lookup"><span data-stu-id="c14fd-119">Text Value</span></span>

<span data-ttu-id="c14fd-120">指定選取項目集的名稱。</span><span class="sxs-lookup"><span data-stu-id="c14fd-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="c14fd-121">備註</span><span class="sxs-lookup"><span data-stu-id="c14fd-121">Remarks</span></span>

<span data-ttu-id="c14fd-122">每個自訂控制項定義必須至少一個型別名稱、 選取項目集或選擇條件的定義。</span><span class="sxs-lookup"><span data-stu-id="c14fd-122">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="c14fd-123">您想要在多個檢視中定義一組所使用的物件時，會通常會使用選取項目集。</span><span class="sxs-lookup"><span data-stu-id="c14fd-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="c14fd-124">例如，您可能要建立資料表檢視和相同的物件集的清單檢視。</span><span class="sxs-lookup"><span data-stu-id="c14fd-124">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="c14fd-125">如需定義選取項目集的詳細資訊，請參閱[定義的選取項目設定](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="c14fd-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="c14fd-126">如需詳細的自訂控制項的檢視元件的相關資訊，請參閱[建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="c14fd-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c14fd-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c14fd-127">See Also</span></span>

[<span data-ttu-id="c14fd-128">GroupBy （格式） 的 CustomEntry EntrySelectedBy 項目</span><span class="sxs-lookup"><span data-stu-id="c14fd-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="c14fd-129">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="c14fd-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="c14fd-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="c14fd-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
