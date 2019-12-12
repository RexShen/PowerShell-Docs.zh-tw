---
title: 設定之控制項的之 entryselectedby 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364787"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="12182-102">設定之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="12182-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="12182-103">指定一組使用此控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="12182-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="12182-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="12182-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="12182-105">Configuration 元素（格式）控制設定（format） CustomControl 元素的設定（格式）控制項專案的設定專案（格式） CustomControl 設定的 CustomEntries 元素（格式）Format） CustomEntry 元素，用於 CustomControl for 控制項的之 entryselectedby 元素（格式為 CustomEntry 的控制項，適用于 configuration （格式） SelectionSetName 元素的控制項）。</span><span class="sxs-lookup"><span data-stu-id="12182-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="12182-106">語法</span><span class="sxs-lookup"><span data-stu-id="12182-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="12182-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="12182-107">Attributes and Elements</span></span>

<span data-ttu-id="12182-108">下列各節說明屬性、子專案，以及 `SelectionSetName` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="12182-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="12182-109">屬性</span><span class="sxs-lookup"><span data-stu-id="12182-109">Attributes</span></span>

<span data-ttu-id="12182-110">無</span><span class="sxs-lookup"><span data-stu-id="12182-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="12182-111">子元素</span><span class="sxs-lookup"><span data-stu-id="12182-111">Child Elements</span></span>

<span data-ttu-id="12182-112">無。</span><span class="sxs-lookup"><span data-stu-id="12182-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="12182-113">父元素</span><span class="sxs-lookup"><span data-stu-id="12182-113">Parent Elements</span></span>

|<span data-ttu-id="12182-114">元素</span><span class="sxs-lookup"><span data-stu-id="12182-114">Element</span></span>|<span data-ttu-id="12182-115">描述</span><span class="sxs-lookup"><span data-stu-id="12182-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="12182-116">設定之控制項的 CustomEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="12182-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="12182-117">定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="12182-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="12182-118">文字值</span><span class="sxs-lookup"><span data-stu-id="12182-118">Text Value</span></span>

<span data-ttu-id="12182-119">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="12182-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="12182-120">備註</span><span class="sxs-lookup"><span data-stu-id="12182-120">Remarks</span></span>

<span data-ttu-id="12182-121">每個控制項定義都必須定義至少一個型別名稱、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="12182-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="12182-122">當您想要定義多個視圖中使用的一組物件時，通常會使用選取範圍集。</span><span class="sxs-lookup"><span data-stu-id="12182-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="12182-123">如需定義選取集的詳細資訊，請參閱[定義選取範圍集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="12182-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="12182-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12182-124">See Also</span></span>

[<span data-ttu-id="12182-125">設定之控制項的 CustomEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="12182-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="12182-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="12182-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
