---
title: CustomControl 檢視 （格式） 的 EntrySelectedBy SelectionSetName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063962"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="62dc2-102">檢視之 CustomControl 的 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="62dc2-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="62dc2-103">指定一組.NET 物件清單項目。</span><span class="sxs-lookup"><span data-stu-id="62dc2-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="62dc2-104">可供指定的項目選取項目集的數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="62dc2-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="62dc2-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目 （格式） CustomEntries 項目 CustomControl 檢視 （格式） 的檢視 （格式） EntrySelectedBy CustomEntries CustomEntry 元素CustomEntry EntrySelectedBy CustomEntry （格式） 的檢視 （格式） SelectionSetName 元素的項目</span><span class="sxs-lookup"><span data-stu-id="62dc2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="62dc2-106">語法</span><span class="sxs-lookup"><span data-stu-id="62dc2-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="62dc2-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="62dc2-107">Attributes and Elements</span></span>

<span data-ttu-id="62dc2-108">下列各節說明屬性、 子項目和父項目`SelectionSetName`項目。</span><span class="sxs-lookup"><span data-stu-id="62dc2-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="62dc2-109">屬性</span><span class="sxs-lookup"><span data-stu-id="62dc2-109">Attributes</span></span>

<span data-ttu-id="62dc2-110">無。</span><span class="sxs-lookup"><span data-stu-id="62dc2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="62dc2-111">子元素</span><span class="sxs-lookup"><span data-stu-id="62dc2-111">Child Elements</span></span>

<span data-ttu-id="62dc2-112">無。</span><span class="sxs-lookup"><span data-stu-id="62dc2-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="62dc2-113">父項目</span><span class="sxs-lookup"><span data-stu-id="62dc2-113">Parent Elements</span></span>

|<span data-ttu-id="62dc2-114">項目</span><span class="sxs-lookup"><span data-stu-id="62dc2-114">Element</span></span>|<span data-ttu-id="62dc2-115">描述</span><span class="sxs-lookup"><span data-stu-id="62dc2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="62dc2-116">EntrySelectedBy CustomEntry 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="62dc2-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="62dc2-117">定義.NET 型別，使用此自訂的項目或要使用此項目必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="62dc2-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="62dc2-118">文字值</span><span class="sxs-lookup"><span data-stu-id="62dc2-118">Text Value</span></span>

<span data-ttu-id="62dc2-119">指定選取項目集的名稱。</span><span class="sxs-lookup"><span data-stu-id="62dc2-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="62dc2-120">備註</span><span class="sxs-lookup"><span data-stu-id="62dc2-120">Remarks</span></span>

<span data-ttu-id="62dc2-121">每個自訂控制項項目必須至少一個型別名稱、 選取項目集或選擇條件的定義。</span><span class="sxs-lookup"><span data-stu-id="62dc2-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="62dc2-122">您想要在多個檢視中定義一組所使用的物件時，會通常會使用選取項目集。</span><span class="sxs-lookup"><span data-stu-id="62dc2-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="62dc2-123">例如，您可能要建立的資料表檢視和相同的物件集的清單檢視。</span><span class="sxs-lookup"><span data-stu-id="62dc2-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="62dc2-124">如需定義選取項目集的詳細資訊，請參閱[定義的選取項目設定](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="62dc2-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="62dc2-125">如需詳細的自訂控制項的檢視元件的相關資訊，請參閱[建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="62dc2-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="62dc2-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62dc2-126">See Also</span></span>

[<span data-ttu-id="62dc2-127">EntrySelectedBy CustomEntry 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="62dc2-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="62dc2-128">自訂的控制項檢視</span><span class="sxs-lookup"><span data-stu-id="62dc2-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="62dc2-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="62dc2-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
