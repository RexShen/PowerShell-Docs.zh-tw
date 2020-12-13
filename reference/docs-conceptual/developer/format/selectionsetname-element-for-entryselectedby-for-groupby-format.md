---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)
description: GroupBy 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: 7ebe5d884061243c8b4af196788187d84c15a92e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651841"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="31fb3-103">GroupBy 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="31fb3-103">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="31fb3-104">指定清單專案的一組 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="31fb3-104">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="31fb3-105">可以針對專案指定的選取範圍數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="31fb3-105">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="31fb3-106">定義如何顯示新的物件群組時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="31fb3-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="31fb3-107">設定元素 (格式) ViewDefinitions 元素 (格式) View 專案 (格式) GroupBy 專案的視圖 (格式) CustomEntries 元素適用于 GroupBy (格式) CustomEntry 專案用於 CustomControl 的 groupby (格式) 之 entryselectedby 專案適用于 CustomEntry 的 groupby (格式)  (</span><span class="sxs-lookup"><span data-stu-id="31fb3-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="31fb3-108">語法</span><span class="sxs-lookup"><span data-stu-id="31fb3-108">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="31fb3-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="31fb3-109">Attributes and Elements</span></span>

<span data-ttu-id="31fb3-110">下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="31fb3-110">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="31fb3-111">屬性</span><span class="sxs-lookup"><span data-stu-id="31fb3-111">Attributes</span></span>

<span data-ttu-id="31fb3-112">無。</span><span class="sxs-lookup"><span data-stu-id="31fb3-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="31fb3-113">子元素</span><span class="sxs-lookup"><span data-stu-id="31fb3-113">Child Elements</span></span>

<span data-ttu-id="31fb3-114">無。</span><span class="sxs-lookup"><span data-stu-id="31fb3-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="31fb3-115">父項目</span><span class="sxs-lookup"><span data-stu-id="31fb3-115">Parent Elements</span></span>

|<span data-ttu-id="31fb3-116">元素</span><span class="sxs-lookup"><span data-stu-id="31fb3-116">Element</span></span>|<span data-ttu-id="31fb3-117">描述</span><span class="sxs-lookup"><span data-stu-id="31fb3-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="31fb3-118">GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="31fb3-118">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="31fb3-119">定義使用此自訂專案的 .NET 型別，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="31fb3-119">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="31fb3-120">文字值</span><span class="sxs-lookup"><span data-stu-id="31fb3-120">Text Value</span></span>

<span data-ttu-id="31fb3-121">指定選項群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="31fb3-121">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="31fb3-122">備註</span><span class="sxs-lookup"><span data-stu-id="31fb3-122">Remarks</span></span>

<span data-ttu-id="31fb3-123">每個自訂控制項定義都必須定義至少一個類型名稱、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="31fb3-123">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="31fb3-124">當您想要定義多個視圖中使用的一組物件時，通常會使用選取集。</span><span class="sxs-lookup"><span data-stu-id="31fb3-124">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="31fb3-125">例如，您可能會想要為相同的物件集建立資料表視圖和清單視圖。</span><span class="sxs-lookup"><span data-stu-id="31fb3-125">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="31fb3-126">如需定義選取範圍的詳細資訊，請參閱 [定義選取集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="31fb3-126">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="31fb3-127">如需自訂控制項視圖元件的詳細資訊，請參閱 [建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="31fb3-127">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="31fb3-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31fb3-128">See Also</span></span>

[<span data-ttu-id="31fb3-129">GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="31fb3-129">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="31fb3-130">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="31fb3-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="31fb3-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="31fb3-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
