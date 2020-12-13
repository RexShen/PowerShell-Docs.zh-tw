---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)
description: 設定之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: b775aa8a3184aa3ebcbda17a8e3191c69d67a700
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645720"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="d4113-103">設定之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d4113-103">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="d4113-104">指定一組使用此控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="d4113-104">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="d4113-105">當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="d4113-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="d4113-106">設定專案 (格式) 控制項設定的控制項專案 (格式設定的控制項) 控制項專案 (格式) CustomEntries 專案的 CustomControl 設定 (格式) 的格式 (格式) CustomControl 專案設定 (格式) 之 entryselectedby 專案 (格式的控制項) 格式 (的控制項的 CustomEntry 元素) </span><span class="sxs-lookup"><span data-stu-id="d4113-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d4113-107">語法</span><span class="sxs-lookup"><span data-stu-id="d4113-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d4113-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d4113-108">Attributes and Elements</span></span>

<span data-ttu-id="d4113-109">下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="d4113-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d4113-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d4113-110">Attributes</span></span>

<span data-ttu-id="d4113-111">無</span><span class="sxs-lookup"><span data-stu-id="d4113-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="d4113-112">子元素</span><span class="sxs-lookup"><span data-stu-id="d4113-112">Child Elements</span></span>

<span data-ttu-id="d4113-113">無。</span><span class="sxs-lookup"><span data-stu-id="d4113-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d4113-114">父項目</span><span class="sxs-lookup"><span data-stu-id="d4113-114">Parent Elements</span></span>

|<span data-ttu-id="d4113-115">元素</span><span class="sxs-lookup"><span data-stu-id="d4113-115">Element</span></span>|<span data-ttu-id="d4113-116">描述</span><span class="sxs-lookup"><span data-stu-id="d4113-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d4113-117">設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d4113-117">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="d4113-118">定義使用此控制項定義的 .NET 型別，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="d4113-118">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d4113-119">文字值</span><span class="sxs-lookup"><span data-stu-id="d4113-119">Text Value</span></span>

<span data-ttu-id="d4113-120">指定選項群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="d4113-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="d4113-121">備註</span><span class="sxs-lookup"><span data-stu-id="d4113-121">Remarks</span></span>

<span data-ttu-id="d4113-122">每個控制項定義都必須定義至少一個類型名稱、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="d4113-122">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="d4113-123">當您想要定義多個視圖中使用的一組物件時，通常會使用選取集。</span><span class="sxs-lookup"><span data-stu-id="d4113-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="d4113-124">如需定義選取範圍的詳細資訊，請參閱 [定義選取集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="d4113-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d4113-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4113-125">See Also</span></span>

[<span data-ttu-id="d4113-126">設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d4113-126">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="d4113-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="d4113-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
