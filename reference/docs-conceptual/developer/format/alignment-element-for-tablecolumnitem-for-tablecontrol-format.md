---
title: TableControl (格式的之 tablecolumnitem 的對齊元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: baa858b7c15b5afcc7f6087e8a9eace8d8fb67bb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783903"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="b47ad-102">TableControl 之 TableColumnItem 的對齊元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b47ad-102">Alignment Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="b47ad-103">定義如何顯示資料列資料行中的資料。</span><span class="sxs-lookup"><span data-stu-id="b47ad-103">Defines how the data in a column of the row is displayed.</span></span>

<span data-ttu-id="b47ad-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 專案 (格式) TableRowEntries 專案 (格式) TableRowEntry 專案 (格式) TableColumnItems 元素 (格式) 之 tablecolumnitem 元素 (格式) 之 tablecolumnitem (格式的對齊元素) </span><span class="sxs-lookup"><span data-stu-id="b47ad-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) Alignment Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b47ad-105">語法</span><span class="sxs-lookup"><span data-stu-id="b47ad-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b47ad-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b47ad-106">Attributes and Elements</span></span>

<span data-ttu-id="b47ad-107">下列各節描述元素的屬性、子專案和父項目 `Alignment` 。</span><span class="sxs-lookup"><span data-stu-id="b47ad-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b47ad-108">屬性</span><span class="sxs-lookup"><span data-stu-id="b47ad-108">Attributes</span></span>

<span data-ttu-id="b47ad-109">無。</span><span class="sxs-lookup"><span data-stu-id="b47ad-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b47ad-110">子元素</span><span class="sxs-lookup"><span data-stu-id="b47ad-110">Child Elements</span></span>

<span data-ttu-id="b47ad-111">無。</span><span class="sxs-lookup"><span data-stu-id="b47ad-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b47ad-112">父項目</span><span class="sxs-lookup"><span data-stu-id="b47ad-112">Parent Elements</span></span>

|<span data-ttu-id="b47ad-113">元素</span><span class="sxs-lookup"><span data-stu-id="b47ad-113">Element</span></span>|<span data-ttu-id="b47ad-114">描述</span><span class="sxs-lookup"><span data-stu-id="b47ad-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b47ad-115">之 tablecolumnitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="b47ad-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="b47ad-116">定義資料表資料行的標籤、寬度和對齊方式。</span><span class="sxs-lookup"><span data-stu-id="b47ad-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b47ad-117">文字值</span><span class="sxs-lookup"><span data-stu-id="b47ad-117">Text Value</span></span>

<span data-ttu-id="b47ad-118">指定下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="b47ad-118">Specify one of the following values.</span></span> <span data-ttu-id="b47ad-119"> (這些值不區分大小寫。 ) </span><span class="sxs-lookup"><span data-stu-id="b47ad-119">(These values are not case-sensitive.)</span></span>

<span data-ttu-id="b47ad-120">Left 會將資料行中顯示的資料移至左邊。</span><span class="sxs-lookup"><span data-stu-id="b47ad-120">Left Shifts the data displayed in the column to the left.</span></span> <span data-ttu-id="b47ad-121"> (如果未指定此元素，則此為預設值。 ) </span><span class="sxs-lookup"><span data-stu-id="b47ad-121">(This is the default if this element is not specified.)</span></span>

<span data-ttu-id="b47ad-122">Right 將資料行中所顯示的資料向右移動。</span><span class="sxs-lookup"><span data-stu-id="b47ad-122">Right Shifts the data displayed in the column to the right.</span></span>

<span data-ttu-id="b47ad-123">置中：在資料行中顯示的資料中心。</span><span class="sxs-lookup"><span data-stu-id="b47ad-123">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="b47ad-124">備註</span><span class="sxs-lookup"><span data-stu-id="b47ad-124">Remarks</span></span>

<span data-ttu-id="b47ad-125">如需有關資料表視圖之元件的詳細資訊，請參閱[資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="b47ad-125">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b47ad-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b47ad-126">See Also</span></span>

[<span data-ttu-id="b47ad-127">資料表視圖</span><span class="sxs-lookup"><span data-stu-id="b47ad-127">Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b47ad-128">之 tablecolumnitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="b47ad-128">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)
