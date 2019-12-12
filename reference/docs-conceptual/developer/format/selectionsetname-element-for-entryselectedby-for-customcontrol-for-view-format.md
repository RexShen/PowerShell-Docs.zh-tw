---
title: CustomControl for View 的之 entryselectedby 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364747"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="3e903-102">檢視之 CustomControl 的 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3e903-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="3e903-103">為清單專案指定一組 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="3e903-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="3e903-104">可以為專案指定的選擇集數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="3e903-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="3e903-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素（format） CustomEntries 元素，適用于 CustomEntry for View 的 CustomControl for View （format） CustomEntries 元素（格式）之 entryselectedbyCustomEntry for View （Format） SelectionSetName 元素的元素，適用于 CustomEntry 的之 entryselectedby （格式）</span><span class="sxs-lookup"><span data-stu-id="3e903-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3e903-106">語法</span><span class="sxs-lookup"><span data-stu-id="3e903-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3e903-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="3e903-107">Attributes and Elements</span></span>

<span data-ttu-id="3e903-108">下列各節說明屬性、子專案，以及 `SelectionSetName` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="3e903-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3e903-109">屬性</span><span class="sxs-lookup"><span data-stu-id="3e903-109">Attributes</span></span>

<span data-ttu-id="3e903-110">無。</span><span class="sxs-lookup"><span data-stu-id="3e903-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3e903-111">子元素</span><span class="sxs-lookup"><span data-stu-id="3e903-111">Child Elements</span></span>

<span data-ttu-id="3e903-112">無。</span><span class="sxs-lookup"><span data-stu-id="3e903-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3e903-113">父元素</span><span class="sxs-lookup"><span data-stu-id="3e903-113">Parent Elements</span></span>

|<span data-ttu-id="3e903-114">元素</span><span class="sxs-lookup"><span data-stu-id="3e903-114">Element</span></span>|<span data-ttu-id="3e903-115">描述</span><span class="sxs-lookup"><span data-stu-id="3e903-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3e903-116">CustomEntry for View 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3e903-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="3e903-117">定義使用此自訂專案的 .NET 類型，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="3e903-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3e903-118">文字值</span><span class="sxs-lookup"><span data-stu-id="3e903-118">Text Value</span></span>

<span data-ttu-id="3e903-119">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="3e903-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="3e903-120">備註</span><span class="sxs-lookup"><span data-stu-id="3e903-120">Remarks</span></span>

<span data-ttu-id="3e903-121">每個自訂控制項專案都必須定義至少一個型別名稱、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="3e903-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="3e903-122">當您想要定義多個視圖中使用的一組物件時，通常會使用選取範圍集。</span><span class="sxs-lookup"><span data-stu-id="3e903-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="3e903-123">例如，您可能會想要建立一組相同物件的資料表視圖和清單視圖。</span><span class="sxs-lookup"><span data-stu-id="3e903-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="3e903-124">如需定義選取集的詳細資訊，請參閱[定義選取範圍集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="3e903-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="3e903-125">如需自訂控制項視圖之元件的詳細資訊，請參閱[建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="3e903-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3e903-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e903-126">See Also</span></span>

[<span data-ttu-id="3e903-127">CustomEntry for View 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3e903-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3e903-128">自訂控制項視圖</span><span class="sxs-lookup"><span data-stu-id="3e903-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="3e903-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="3e903-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
