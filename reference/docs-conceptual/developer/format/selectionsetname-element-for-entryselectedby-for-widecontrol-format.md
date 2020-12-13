---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)
description: WideControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: bf6a44bb733421f36a9140d0ec10e61aedfbda6a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651692"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="a6418-103">WideControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a6418-103">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="a6418-104">指定定義的一組 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="a6418-104">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="a6418-105">每當顯示這些物件的其中一個時，就會使用定義。</span><span class="sxs-lookup"><span data-stu-id="a6418-105">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="a6418-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) WideControl 元素 (格式) WideEntries 元素 (格式) WideEntry 專案 (格式) 之 entryselectedby 專案 (格式) WideEntry 專案 SelectionSetName 的之 entryselectedby (格式) </span><span class="sxs-lookup"><span data-stu-id="a6418-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a6418-107">語法</span><span class="sxs-lookup"><span data-stu-id="a6418-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="a6418-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a6418-108">Attributes and Elements</span></span>

<span data-ttu-id="a6418-109">下列章節說明屬性、子專案和元素的父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="a6418-109">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a6418-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a6418-110">Attributes</span></span>

<span data-ttu-id="a6418-111">無。</span><span class="sxs-lookup"><span data-stu-id="a6418-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a6418-112">子元素</span><span class="sxs-lookup"><span data-stu-id="a6418-112">Child Elements</span></span>

<span data-ttu-id="a6418-113">無。</span><span class="sxs-lookup"><span data-stu-id="a6418-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a6418-114">父項目</span><span class="sxs-lookup"><span data-stu-id="a6418-114">Parent Elements</span></span>

|<span data-ttu-id="a6418-115">元素</span><span class="sxs-lookup"><span data-stu-id="a6418-115">Element</span></span>|<span data-ttu-id="a6418-116">描述</span><span class="sxs-lookup"><span data-stu-id="a6418-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a6418-117">WideEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a6418-117">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="a6418-118">定義使用此寬專案的 .NET 型別，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="a6418-118">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a6418-119">文字值</span><span class="sxs-lookup"><span data-stu-id="a6418-119">Text Value</span></span>

<span data-ttu-id="a6418-120">指定選項群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="a6418-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="a6418-121">備註</span><span class="sxs-lookup"><span data-stu-id="a6418-121">Remarks</span></span>

<span data-ttu-id="a6418-122">每個定義都必須指定一個類型名稱、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="a6418-122">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="a6418-123">當您想要定義多個視圖中使用的一組物件時，通常會使用選取集。</span><span class="sxs-lookup"><span data-stu-id="a6418-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="a6418-124">例如，您可能會想要為相同的物件集建立資料表視圖和清單視圖。</span><span class="sxs-lookup"><span data-stu-id="a6418-124">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="a6418-125">如需定義選擇集的詳細資訊，請參閱 [定義視圖的物件集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="a6418-125">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="a6418-126">如需更多有關廣泛視圖的元件的詳細資訊，請參閱 [建立廣泛的觀點](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="a6418-126">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a6418-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6418-127">See Also</span></span>

[<span data-ttu-id="a6418-128">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="a6418-128">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="a6418-129">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="a6418-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="a6418-130">WideEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a6418-130">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="a6418-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="a6418-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
