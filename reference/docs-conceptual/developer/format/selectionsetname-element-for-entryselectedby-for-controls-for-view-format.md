---
title: View 之控制項的之 entryselectedby 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b594a064-746f-4900-99e4-7be7bf5aa5a2
caps.latest.revision: 7
ms.openlocfilehash: d540c99707f4e0796b2d408f2161a9208257ab32
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368347"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="aaeb8-102">檢視之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="aaeb8-102">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="aaeb8-103">指定一組使用此控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="aaeb8-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="aaeb8-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="aaeb8-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="aaeb8-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素CustomControl for view （format） CustomEntry 元素的 CustomEntries for view （format）之 entryselectedby 元素 for CustomEntry for view （format） SelectionSetName 元素 for controls 的控制項（格式）編排</span><span class="sxs-lookup"><span data-stu-id="aaeb8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aaeb8-106">語法</span><span class="sxs-lookup"><span data-stu-id="aaeb8-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="aaeb8-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="aaeb8-107">Attributes and Elements</span></span>

<span data-ttu-id="aaeb8-108">下列各節說明屬性、子專案，以及 `SelectionSetName` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="aaeb8-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aaeb8-109">屬性</span><span class="sxs-lookup"><span data-stu-id="aaeb8-109">Attributes</span></span>

<span data-ttu-id="aaeb8-110">無</span><span class="sxs-lookup"><span data-stu-id="aaeb8-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="aaeb8-111">子元素</span><span class="sxs-lookup"><span data-stu-id="aaeb8-111">Child Elements</span></span>

<span data-ttu-id="aaeb8-112">無。</span><span class="sxs-lookup"><span data-stu-id="aaeb8-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="aaeb8-113">父元素</span><span class="sxs-lookup"><span data-stu-id="aaeb8-113">Parent Elements</span></span>

|<span data-ttu-id="aaeb8-114">元素</span><span class="sxs-lookup"><span data-stu-id="aaeb8-114">Element</span></span>|<span data-ttu-id="aaeb8-115">描述</span><span class="sxs-lookup"><span data-stu-id="aaeb8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aaeb8-116">View 之控制項的 CustomEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="aaeb8-116">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="aaeb8-117">定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="aaeb8-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="aaeb8-118">文字值</span><span class="sxs-lookup"><span data-stu-id="aaeb8-118">Text Value</span></span>

<span data-ttu-id="aaeb8-119">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="aaeb8-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="aaeb8-120">備註</span><span class="sxs-lookup"><span data-stu-id="aaeb8-120">Remarks</span></span>

<span data-ttu-id="aaeb8-121">每個控制項定義都必須定義至少一個型別名稱、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="aaeb8-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="aaeb8-122">當您想要定義多個視圖中使用的一組物件時，通常會使用選取範圍集。</span><span class="sxs-lookup"><span data-stu-id="aaeb8-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="aaeb8-123">如需定義選取集的詳細資訊，請參閱[定義選取範圍集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="aaeb8-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aaeb8-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aaeb8-124">See Also</span></span>

[<span data-ttu-id="aaeb8-125">View 之控制項的 CustomEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="aaeb8-125">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="aaeb8-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="aaeb8-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
