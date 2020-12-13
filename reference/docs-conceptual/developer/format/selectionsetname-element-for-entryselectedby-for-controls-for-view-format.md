---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)
description: 檢視之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: 3211b7cacd7e57770b48b03f4aade33da506f180
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664733"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="2f6ba-103">檢視之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2f6ba-103">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="2f6ba-104">指定一組使用此控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="2f6ba-104">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="2f6ba-105">當定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="2f6ba-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="2f6ba-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 專案 (格式) 控制項專案 (格式) 控制項專案 (格式控制項的控制項) 格式 (CustomEntries 元素 view (格式的控制項 CustomControl) CustomEntry 專案的 CustomEntries 控制項，適用于 view 的格式) 之 entryselectedby (格式的控制項) 格式 (CustomEntry 專案) 格式的控制項 (</span><span class="sxs-lookup"><span data-stu-id="2f6ba-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2f6ba-107">語法</span><span class="sxs-lookup"><span data-stu-id="2f6ba-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="2f6ba-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2f6ba-108">Attributes and Elements</span></span>

<span data-ttu-id="2f6ba-109">下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="2f6ba-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2f6ba-110">屬性</span><span class="sxs-lookup"><span data-stu-id="2f6ba-110">Attributes</span></span>

<span data-ttu-id="2f6ba-111">無</span><span class="sxs-lookup"><span data-stu-id="2f6ba-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="2f6ba-112">子元素</span><span class="sxs-lookup"><span data-stu-id="2f6ba-112">Child Elements</span></span>

<span data-ttu-id="2f6ba-113">無。</span><span class="sxs-lookup"><span data-stu-id="2f6ba-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2f6ba-114">父項目</span><span class="sxs-lookup"><span data-stu-id="2f6ba-114">Parent Elements</span></span>

|<span data-ttu-id="2f6ba-115">元素</span><span class="sxs-lookup"><span data-stu-id="2f6ba-115">Element</span></span>|<span data-ttu-id="2f6ba-116">描述</span><span class="sxs-lookup"><span data-stu-id="2f6ba-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2f6ba-117">檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2f6ba-117">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="2f6ba-118">定義使用此控制項定義的 .NET 型別，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="2f6ba-118">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2f6ba-119">文字值</span><span class="sxs-lookup"><span data-stu-id="2f6ba-119">Text Value</span></span>

<span data-ttu-id="2f6ba-120">指定選項群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="2f6ba-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="2f6ba-121">備註</span><span class="sxs-lookup"><span data-stu-id="2f6ba-121">Remarks</span></span>

<span data-ttu-id="2f6ba-122">每個控制項定義都必須定義至少一個類型名稱、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="2f6ba-122">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="2f6ba-123">當您想要定義多個視圖中使用的一組物件時，通常會使用選取集。</span><span class="sxs-lookup"><span data-stu-id="2f6ba-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="2f6ba-124">如需定義選取範圍的詳細資訊，請參閱 [定義選取集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="2f6ba-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2f6ba-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f6ba-125">See Also</span></span>

[<span data-ttu-id="2f6ba-126">檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2f6ba-126">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="2f6ba-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="2f6ba-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
