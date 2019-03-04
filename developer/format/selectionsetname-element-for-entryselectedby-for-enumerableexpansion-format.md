---
title: EnumerableExpansion （格式） 的 EntrySelectedBy SelectionSetName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862744"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="f8a3e-102">EnumerableExpansion 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="f8a3e-102">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="f8a3e-103">指定.NET 型別，此定義會擴展集。</span><span class="sxs-lookup"><span data-stu-id="f8a3e-103">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="f8a3e-104">組態項目 （格式） DefaultSettings 項目 （格式） EnumerableExpansions 項目 （格式） EnumerableExpansion 項目 （格式） EntrySelectedBy 項目為 EntrySelectedBy EnumerableExpansion （格式） SelectionSetName 項目EnumerableExpansion （格式）</span><span class="sxs-lookup"><span data-stu-id="f8a3e-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f8a3e-105">語法</span><span class="sxs-lookup"><span data-stu-id="f8a3e-105">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="f8a3e-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="f8a3e-106">Attributes and Elements</span></span>

<span data-ttu-id="f8a3e-107">下列各節說明屬性、 子項目和父項目`SelectionSetName`項目。</span><span class="sxs-lookup"><span data-stu-id="f8a3e-107">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f8a3e-108">屬性</span><span class="sxs-lookup"><span data-stu-id="f8a3e-108">Attributes</span></span>

<span data-ttu-id="f8a3e-109">無。</span><span class="sxs-lookup"><span data-stu-id="f8a3e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f8a3e-110">子元素</span><span class="sxs-lookup"><span data-stu-id="f8a3e-110">Child Elements</span></span>

<span data-ttu-id="f8a3e-111">無。</span><span class="sxs-lookup"><span data-stu-id="f8a3e-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f8a3e-112">父元素</span><span class="sxs-lookup"><span data-stu-id="f8a3e-112">Parent Elements</span></span>

|<span data-ttu-id="f8a3e-113">元素</span><span class="sxs-lookup"><span data-stu-id="f8a3e-113">Element</span></span>|<span data-ttu-id="f8a3e-114">描述</span><span class="sxs-lookup"><span data-stu-id="f8a3e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f8a3e-115">EntrySelectedBy EnumerableExpansion （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="f8a3e-115">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="f8a3e-116">定義根據這個定義會展開的.NET 集合物件。</span><span class="sxs-lookup"><span data-stu-id="f8a3e-116">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f8a3e-117">文字值</span><span class="sxs-lookup"><span data-stu-id="f8a3e-117">Text Value</span></span>

<span data-ttu-id="f8a3e-118">指定選取項目集的名稱。</span><span class="sxs-lookup"><span data-stu-id="f8a3e-118">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="f8a3e-119">備註</span><span class="sxs-lookup"><span data-stu-id="f8a3e-119">Remarks</span></span>

<span data-ttu-id="f8a3e-120">每個定義必須指定一或多個型別名稱、 選取項目集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="f8a3e-120">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="f8a3e-121">您想要在多個檢視中定義一組所使用的物件時，會通常會使用選取項目集。</span><span class="sxs-lookup"><span data-stu-id="f8a3e-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="f8a3e-122">例如，您可能要建立的資料表檢視和相同的物件集的清單檢視。</span><span class="sxs-lookup"><span data-stu-id="f8a3e-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="f8a3e-123">如需定義選取項目集的詳細資訊，請參閱[定義設定的物件檢視](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="f8a3e-123">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f8a3e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8a3e-124">See Also</span></span>

[<span data-ttu-id="f8a3e-125">定義選取範圍</span><span class="sxs-lookup"><span data-stu-id="f8a3e-125">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="f8a3e-126">EntrySelectedBy EnumerableExpansion （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="f8a3e-126">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="f8a3e-127">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="f8a3e-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
