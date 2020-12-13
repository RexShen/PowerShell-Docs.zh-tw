---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 TableColumnItem 的對齊元素 (格式)
description: TableControl 之 TableColumnItem 的對齊元素 (格式)
ms.openlocfilehash: d2bb81ff894cad44e16212891faffd22ee627383
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646111"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="a17b2-103">TableControl 之 TableColumnItem 的對齊元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a17b2-103">Alignment Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="a17b2-104">定義如何顯示資料列資料行中的資料。</span><span class="sxs-lookup"><span data-stu-id="a17b2-104">Defines how the data in a column of the row is displayed.</span></span>

<span data-ttu-id="a17b2-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) TableRowEntries 元素 (格式) TableRowEntry 專案 (格式) TableColumnItems 專案 (格式) 之 tablecolumnitem 專案 (格式)  () 格式對齊元素</span><span class="sxs-lookup"><span data-stu-id="a17b2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) Alignment Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a17b2-106">語法</span><span class="sxs-lookup"><span data-stu-id="a17b2-106">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a17b2-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a17b2-107">Attributes and Elements</span></span>

<span data-ttu-id="a17b2-108">下列各節描述專案的屬性、子項目和父元素 `Alignment` 。</span><span class="sxs-lookup"><span data-stu-id="a17b2-108">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a17b2-109">屬性</span><span class="sxs-lookup"><span data-stu-id="a17b2-109">Attributes</span></span>

<span data-ttu-id="a17b2-110">無。</span><span class="sxs-lookup"><span data-stu-id="a17b2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a17b2-111">子元素</span><span class="sxs-lookup"><span data-stu-id="a17b2-111">Child Elements</span></span>

<span data-ttu-id="a17b2-112">無。</span><span class="sxs-lookup"><span data-stu-id="a17b2-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a17b2-113">父項目</span><span class="sxs-lookup"><span data-stu-id="a17b2-113">Parent Elements</span></span>

|<span data-ttu-id="a17b2-114">元素</span><span class="sxs-lookup"><span data-stu-id="a17b2-114">Element</span></span>|<span data-ttu-id="a17b2-115">描述</span><span class="sxs-lookup"><span data-stu-id="a17b2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a17b2-116">之 tablecolumnitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="a17b2-116">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="a17b2-117">定義資料表之資料行的標籤、寬度和對齊方式。</span><span class="sxs-lookup"><span data-stu-id="a17b2-117">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a17b2-118">文字值</span><span class="sxs-lookup"><span data-stu-id="a17b2-118">Text Value</span></span>

<span data-ttu-id="a17b2-119">指定下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="a17b2-119">Specify one of the following values.</span></span> <span data-ttu-id="a17b2-120"> (這些值不區分大小寫。 ) </span><span class="sxs-lookup"><span data-stu-id="a17b2-120">(These values are not case-sensitive.)</span></span>

<span data-ttu-id="a17b2-121">將資料行中顯示的資料向左移動。</span><span class="sxs-lookup"><span data-stu-id="a17b2-121">Left Shifts the data displayed in the column to the left.</span></span> <span data-ttu-id="a17b2-122"> (如果未指定此元素，這是預設值。 ) </span><span class="sxs-lookup"><span data-stu-id="a17b2-122">(This is the default if this element is not specified.)</span></span>

<span data-ttu-id="a17b2-123">Right 會將資料行中顯示的資料向右移動。</span><span class="sxs-lookup"><span data-stu-id="a17b2-123">Right Shifts the data displayed in the column to the right.</span></span>

<span data-ttu-id="a17b2-124">置中：將資料行中顯示的資料置中。</span><span class="sxs-lookup"><span data-stu-id="a17b2-124">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="a17b2-125">備註</span><span class="sxs-lookup"><span data-stu-id="a17b2-125">Remarks</span></span>

<span data-ttu-id="a17b2-126">如需有關資料表視圖元件的詳細資訊，請參閱 [資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="a17b2-126">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a17b2-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a17b2-127">See Also</span></span>

[<span data-ttu-id="a17b2-128">資料表視圖</span><span class="sxs-lookup"><span data-stu-id="a17b2-128">Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a17b2-129">之 tablecolumnitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="a17b2-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)
