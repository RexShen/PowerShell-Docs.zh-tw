---
title: WideControl (格式) 的之 entryselectedby 的 SelectionSetName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 546225b0619ebec83d04a7e27bbc298ffef0a14d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785246"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="588d9-102">WideControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="588d9-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="588d9-103">為定義指定一組 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="588d9-103">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="588d9-104">每當顯示這些物件的其中一個時，就會使用定義。</span><span class="sxs-lookup"><span data-stu-id="588d9-104">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="588d9-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 專案 (格式) WideEntries 專案 (格式) WideEntry 專案 (格式) 之 entryselectedby 元素用於 WideEntry (格式) SelectionSetName 元素 (</span><span class="sxs-lookup"><span data-stu-id="588d9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="588d9-106">語法</span><span class="sxs-lookup"><span data-stu-id="588d9-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="588d9-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="588d9-107">Attributes and Elements</span></span>

<span data-ttu-id="588d9-108">下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="588d9-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="588d9-109">屬性</span><span class="sxs-lookup"><span data-stu-id="588d9-109">Attributes</span></span>

<span data-ttu-id="588d9-110">無。</span><span class="sxs-lookup"><span data-stu-id="588d9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="588d9-111">子元素</span><span class="sxs-lookup"><span data-stu-id="588d9-111">Child Elements</span></span>

<span data-ttu-id="588d9-112">無。</span><span class="sxs-lookup"><span data-stu-id="588d9-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="588d9-113">父項目</span><span class="sxs-lookup"><span data-stu-id="588d9-113">Parent Elements</span></span>

|<span data-ttu-id="588d9-114">元素</span><span class="sxs-lookup"><span data-stu-id="588d9-114">Element</span></span>|<span data-ttu-id="588d9-115">描述</span><span class="sxs-lookup"><span data-stu-id="588d9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="588d9-116">WideEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="588d9-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="588d9-117">定義使用此寬專案的 .NET 類型，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="588d9-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="588d9-118">文字值</span><span class="sxs-lookup"><span data-stu-id="588d9-118">Text Value</span></span>

<span data-ttu-id="588d9-119">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="588d9-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="588d9-120">備註</span><span class="sxs-lookup"><span data-stu-id="588d9-120">Remarks</span></span>

<span data-ttu-id="588d9-121">每個定義都必須指定一個型別名稱、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="588d9-121">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="588d9-122">當您想要定義多個視圖中使用的一組物件時，通常會使用選取範圍集。</span><span class="sxs-lookup"><span data-stu-id="588d9-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="588d9-123">例如，您可能會想要建立一組相同物件的資料表視圖和清單視圖。</span><span class="sxs-lookup"><span data-stu-id="588d9-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="588d9-124">如需定義選取集的詳細資訊，請參閱[定義視圖的物件集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="588d9-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="588d9-125">如需有關寬視圖之其他元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="588d9-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="588d9-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="588d9-126">See Also</span></span>

[<span data-ttu-id="588d9-127">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="588d9-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="588d9-128">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="588d9-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="588d9-129">WideEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="588d9-129">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="588d9-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="588d9-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
