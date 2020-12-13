---
ms.date: 09/13/2016
ms.topic: reference
title: TableColumnHeader 元素 (格式)
description: TableColumnHeader 元素 (格式)
ms.openlocfilehash: 30368512875b7c5c4cf3c686f3d09540dea1bd26
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651526"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="d3c7d-103">TableColumnHeader 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d3c7d-103">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="d3c7d-104">定義標籤、資料行的寬度，以及資料表資料行之標籤的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="d3c7d-104">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="d3c7d-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) TableControl 元素 (format) TableHeaders 元素 for TableControl (Format) 之 tablecolumnheader 元素 for TableHeaders for TableControl (格式) </span><span class="sxs-lookup"><span data-stu-id="d3c7d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d3c7d-106">語法</span><span class="sxs-lookup"><span data-stu-id="d3c7d-106">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d3c7d-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d3c7d-107">Attributes and Elements</span></span>

<span data-ttu-id="d3c7d-108">下列各節說明屬性、子專案和元素的父元素 `TableColumnHeader` 。</span><span class="sxs-lookup"><span data-stu-id="d3c7d-108">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d3c7d-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d3c7d-109">Attributes</span></span>

<span data-ttu-id="d3c7d-110">無。</span><span class="sxs-lookup"><span data-stu-id="d3c7d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d3c7d-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d3c7d-111">Child Elements</span></span>

|<span data-ttu-id="d3c7d-112">元素</span><span class="sxs-lookup"><span data-stu-id="d3c7d-112">Element</span></span>|<span data-ttu-id="d3c7d-113">描述</span><span class="sxs-lookup"><span data-stu-id="d3c7d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d3c7d-114">適用于 TableControl (格式的之 tablecolumnheader 標籤元素) </span><span class="sxs-lookup"><span data-stu-id="d3c7d-114">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="d3c7d-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="d3c7d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="d3c7d-116">定義顯示在資料行頂端的標籤。</span><span class="sxs-lookup"><span data-stu-id="d3c7d-116">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="d3c7d-117">如果未指定標籤，則會使用其值顯示在資料列中的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="d3c7d-117">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="d3c7d-118">TableControl 之 TableColumnHeader 的寬度元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d3c7d-118">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="d3c7d-119">必要元素。</span><span class="sxs-lookup"><span data-stu-id="d3c7d-119">Required element.</span></span><br /><br /> <span data-ttu-id="d3c7d-120">指定資料行的寬度 (字元) 。</span><span class="sxs-lookup"><span data-stu-id="d3c7d-120">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="d3c7d-121">TableControl 之 TableColumnHeader 的對齊元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d3c7d-121">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="d3c7d-122">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="d3c7d-122">Optional element.</span></span><br /><br /> <span data-ttu-id="d3c7d-123">指定如何顯示資料行的標籤。</span><span class="sxs-lookup"><span data-stu-id="d3c7d-123">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="d3c7d-124">如果未指定對齊，則標籤會在左邊對齊。</span><span class="sxs-lookup"><span data-stu-id="d3c7d-124">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d3c7d-125">父項目</span><span class="sxs-lookup"><span data-stu-id="d3c7d-125">Parent Elements</span></span>

|<span data-ttu-id="d3c7d-126">元素</span><span class="sxs-lookup"><span data-stu-id="d3c7d-126">Element</span></span>|<span data-ttu-id="d3c7d-127">描述</span><span class="sxs-lookup"><span data-stu-id="d3c7d-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d3c7d-128">TableHeaders 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d3c7d-128">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="d3c7d-129">定義資料表視圖的資料行。</span><span class="sxs-lookup"><span data-stu-id="d3c7d-129">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d3c7d-130">備註</span><span class="sxs-lookup"><span data-stu-id="d3c7d-130">Remarks</span></span>

<span data-ttu-id="d3c7d-131">針對資料表的每個資料行指定標頭。</span><span class="sxs-lookup"><span data-stu-id="d3c7d-131">Specify a header for each column of the table.</span></span> <span data-ttu-id="d3c7d-132">這些資料行會依照定義專案的順序來顯示 `TableColumnHeader` 。</span><span class="sxs-lookup"><span data-stu-id="d3c7d-132">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="d3c7d-133">資料表的元素數目必須與元素相同 `TableColumnHeader` `TableRowEntry` 。</span><span class="sxs-lookup"><span data-stu-id="d3c7d-133">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="d3c7d-134">資料行標頭會定義資料表頂端的文字顯示方式。</span><span class="sxs-lookup"><span data-stu-id="d3c7d-134">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="d3c7d-135">資料列專案會定義資料表的資料列中所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="d3c7d-135">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="d3c7d-136">如需有關資料表視圖元件的詳細資訊，請參閱 [資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d3c7d-136">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d3c7d-137">範例</span><span class="sxs-lookup"><span data-stu-id="d3c7d-137">Example</span></span>

<span data-ttu-id="d3c7d-138">下列範例顯示兩個 `TableColumnHeader` 元素。</span><span class="sxs-lookup"><span data-stu-id="d3c7d-138">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="d3c7d-139">第一個元素會定義其標籤為「資料行1」、寬度為16個字元，且其標籤在左邊對齊的資料行。</span><span class="sxs-lookup"><span data-stu-id="d3c7d-139">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="d3c7d-140">第二個元素會定義其標籤為「資料行2」、寬度為10個字元，且其標籤在資料行中置中的資料行。</span><span class="sxs-lookup"><span data-stu-id="d3c7d-140">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
    <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a><span data-ttu-id="d3c7d-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3c7d-141">See Also</span></span>

[<span data-ttu-id="d3c7d-142">TableControl 之 TableColumnHeader 的對齊元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d3c7d-142">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="d3c7d-143">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="d3c7d-143">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d3c7d-144">TableControl 之 TableColumnHeader 的標籤元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d3c7d-144">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="d3c7d-145">TableControl (格式的 TableHeaders 元素) </span><span class="sxs-lookup"><span data-stu-id="d3c7d-145">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="d3c7d-146">TableControl 元素的之 tablecolumnheader 寬度 (格式) </span><span class="sxs-lookup"><span data-stu-id="d3c7d-146">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="d3c7d-147">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="d3c7d-147">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
