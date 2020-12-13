---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansion 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)
description: EnumerableExpansion 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: 074f810f5a3cbad61ee8be69408967758f0591df
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651883"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="32c9f-103">EnumerableExpansion 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="32c9f-103">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="32c9f-104">指定由這個定義擴充的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="32c9f-104">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="32c9f-105">設定元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 專案 (格式) EnumerableExpansion 元素 (格式) 之 entryselectedby 專案的 EnumerableExpansion (格式) SelectionSetName 專案之 entryselectedby 的 EnumerableExpansion (格式) </span><span class="sxs-lookup"><span data-stu-id="32c9f-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="32c9f-106">語法</span><span class="sxs-lookup"><span data-stu-id="32c9f-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="32c9f-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="32c9f-107">Attributes and Elements</span></span>

<span data-ttu-id="32c9f-108">下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="32c9f-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="32c9f-109">屬性</span><span class="sxs-lookup"><span data-stu-id="32c9f-109">Attributes</span></span>

<span data-ttu-id="32c9f-110">無。</span><span class="sxs-lookup"><span data-stu-id="32c9f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="32c9f-111">子元素</span><span class="sxs-lookup"><span data-stu-id="32c9f-111">Child Elements</span></span>

<span data-ttu-id="32c9f-112">無。</span><span class="sxs-lookup"><span data-stu-id="32c9f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="32c9f-113">父項目</span><span class="sxs-lookup"><span data-stu-id="32c9f-113">Parent Elements</span></span>

|<span data-ttu-id="32c9f-114">元素</span><span class="sxs-lookup"><span data-stu-id="32c9f-114">Element</span></span>|<span data-ttu-id="32c9f-115">描述</span><span class="sxs-lookup"><span data-stu-id="32c9f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="32c9f-116">EnumerableExpansion 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="32c9f-116">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="32c9f-117">定義由這個定義擴充的 .NET 集合物件。</span><span class="sxs-lookup"><span data-stu-id="32c9f-117">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="32c9f-118">文字值</span><span class="sxs-lookup"><span data-stu-id="32c9f-118">Text Value</span></span>

<span data-ttu-id="32c9f-119">指定選項群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="32c9f-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="32c9f-120">備註</span><span class="sxs-lookup"><span data-stu-id="32c9f-120">Remarks</span></span>

<span data-ttu-id="32c9f-121">每個定義都必須指定一個或多個類型名稱、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="32c9f-121">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="32c9f-122">當您想要定義多個視圖中使用的一組物件時，通常會使用選取集。</span><span class="sxs-lookup"><span data-stu-id="32c9f-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="32c9f-123">例如，您可能會想要為相同的物件集建立資料表視圖和清單視圖。</span><span class="sxs-lookup"><span data-stu-id="32c9f-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="32c9f-124">如需定義選擇集的詳細資訊，請參閱 [定義視圖的物件集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="32c9f-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="32c9f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32c9f-125">See Also</span></span>

[<span data-ttu-id="32c9f-126">定義選取範圍集合</span><span class="sxs-lookup"><span data-stu-id="32c9f-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="32c9f-127">EnumerableExpansion 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="32c9f-127">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="32c9f-128">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="32c9f-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
