---
title: TableControl 之之 tablecolumnitem 的對齊元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b07a53df-64f1-49b0-8cea-c993b3f1f76b
caps.latest.revision: 10
ms.openlocfilehash: 1bc936b94ee6fd6239e9e3c4afcdb8f14fbe36eb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369077"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="fca22-102">TableControl 之 TableColumnItem 的對齊元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fca22-102">Alignment Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="fca22-103">定義如何顯示資料列資料行中的資料。</span><span class="sxs-lookup"><span data-stu-id="fca22-103">Defines how the data in a column of the row is displayed.</span></span>

<span data-ttu-id="fca22-104">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（格式） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（格式） TableColumnItems 元素（格式）之 tablecolumnitem 元素（格式）之 tablecolumnitem 的對齊元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fca22-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) Alignment Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fca22-105">語法</span><span class="sxs-lookup"><span data-stu-id="fca22-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fca22-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="fca22-106">Attributes and Elements</span></span>

<span data-ttu-id="fca22-107">下列各節說明 `Alignment` 元素的屬性、子專案和父元素。</span><span class="sxs-lookup"><span data-stu-id="fca22-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fca22-108">屬性</span><span class="sxs-lookup"><span data-stu-id="fca22-108">Attributes</span></span>

<span data-ttu-id="fca22-109">無。</span><span class="sxs-lookup"><span data-stu-id="fca22-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fca22-110">子元素</span><span class="sxs-lookup"><span data-stu-id="fca22-110">Child Elements</span></span>

<span data-ttu-id="fca22-111">無。</span><span class="sxs-lookup"><span data-stu-id="fca22-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fca22-112">父元素</span><span class="sxs-lookup"><span data-stu-id="fca22-112">Parent Elements</span></span>

|<span data-ttu-id="fca22-113">元素</span><span class="sxs-lookup"><span data-stu-id="fca22-113">Element</span></span>|<span data-ttu-id="fca22-114">描述</span><span class="sxs-lookup"><span data-stu-id="fca22-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fca22-115">之 tablecolumnitem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fca22-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="fca22-116">定義資料表資料行的標籤、寬度和對齊方式。</span><span class="sxs-lookup"><span data-stu-id="fca22-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fca22-117">文字值</span><span class="sxs-lookup"><span data-stu-id="fca22-117">Text Value</span></span>

<span data-ttu-id="fca22-118">指定下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="fca22-118">Specify one of the following values.</span></span> <span data-ttu-id="fca22-119">（這些值不區分大小寫）。</span><span class="sxs-lookup"><span data-stu-id="fca22-119">(These values are not case-sensitive.)</span></span>

<span data-ttu-id="fca22-120">Left 會將資料行中顯示的資料移至左邊。</span><span class="sxs-lookup"><span data-stu-id="fca22-120">Left Shifts the data displayed in the column to the left.</span></span> <span data-ttu-id="fca22-121">（如果未指定這個元素，這就是預設值）。</span><span class="sxs-lookup"><span data-stu-id="fca22-121">(This is the default if this element is not specified.)</span></span>

<span data-ttu-id="fca22-122">Right 將資料行中所顯示的資料向右移動。</span><span class="sxs-lookup"><span data-stu-id="fca22-122">Right Shifts the data displayed in the column to the right.</span></span>

<span data-ttu-id="fca22-123">置中：在資料行中顯示的資料中心。</span><span class="sxs-lookup"><span data-stu-id="fca22-123">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="fca22-124">備註</span><span class="sxs-lookup"><span data-stu-id="fca22-124">Remarks</span></span>

<span data-ttu-id="fca22-125">如需有關資料表視圖之元件的詳細資訊，請參閱[資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="fca22-125">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fca22-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fca22-126">See Also</span></span>

[<span data-ttu-id="fca22-127">資料表視圖</span><span class="sxs-lookup"><span data-stu-id="fca22-127">Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="fca22-128">之 tablecolumnitem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fca22-128">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)
