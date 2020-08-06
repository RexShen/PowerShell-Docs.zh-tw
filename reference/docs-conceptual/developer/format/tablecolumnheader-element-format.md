---
title: 之 tablecolumnheader 元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6296aea5c567663b1c3c0a2cf0a57b21aa5394de
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785178"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="eb962-102">TableColumnHeader 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="eb962-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="eb962-103">定義標籤、資料行的寬度，以及資料表資料行的標籤對齊方式。</span><span class="sxs-lookup"><span data-stu-id="eb962-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="eb962-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 專案 (格式) TableControl (格式) 之 tablecolumnheader 元素用於 TableHeaders 的 TableControl (格式) </span><span class="sxs-lookup"><span data-stu-id="eb962-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="eb962-105">語法</span><span class="sxs-lookup"><span data-stu-id="eb962-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="eb962-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="eb962-106">Attributes and Elements</span></span>

<span data-ttu-id="eb962-107">下列各節說明屬性、子專案和元素的父元素 `TableColumnHeader` 。</span><span class="sxs-lookup"><span data-stu-id="eb962-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="eb962-108">屬性</span><span class="sxs-lookup"><span data-stu-id="eb962-108">Attributes</span></span>

<span data-ttu-id="eb962-109">無。</span><span class="sxs-lookup"><span data-stu-id="eb962-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="eb962-110">子元素</span><span class="sxs-lookup"><span data-stu-id="eb962-110">Child Elements</span></span>

|<span data-ttu-id="eb962-111">元素</span><span class="sxs-lookup"><span data-stu-id="eb962-111">Element</span></span>|<span data-ttu-id="eb962-112">描述</span><span class="sxs-lookup"><span data-stu-id="eb962-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eb962-113">TableControl (格式之之 tablecolumnheader 的 Label 元素) </span><span class="sxs-lookup"><span data-stu-id="eb962-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="eb962-114">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="eb962-114">Optional element.</span></span><br /><br /> <span data-ttu-id="eb962-115">定義顯示在資料行頂端的標籤。</span><span class="sxs-lookup"><span data-stu-id="eb962-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="eb962-116">如果未指定任何標籤，則會使用其值顯示在資料列中的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="eb962-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="eb962-117">TableControl 之 TableColumnHeader 的寬度元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="eb962-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="eb962-118">必要元素。</span><span class="sxs-lookup"><span data-stu-id="eb962-118">Required element.</span></span><br /><br /> <span data-ttu-id="eb962-119">指定資料行的字元) 寬度 (。</span><span class="sxs-lookup"><span data-stu-id="eb962-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="eb962-120">TableControl 之 TableColumnHeader 的對齊元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="eb962-120">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="eb962-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="eb962-121">Optional element.</span></span><br /><br /> <span data-ttu-id="eb962-122">指定資料行標籤的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="eb962-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="eb962-123">如果未指定對齊，標籤會在左邊對齊。</span><span class="sxs-lookup"><span data-stu-id="eb962-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="eb962-124">父項目</span><span class="sxs-lookup"><span data-stu-id="eb962-124">Parent Elements</span></span>

|<span data-ttu-id="eb962-125">元素</span><span class="sxs-lookup"><span data-stu-id="eb962-125">Element</span></span>|<span data-ttu-id="eb962-126">描述</span><span class="sxs-lookup"><span data-stu-id="eb962-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eb962-127">TableHeaders 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="eb962-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="eb962-128">定義資料表視圖的資料行。</span><span class="sxs-lookup"><span data-stu-id="eb962-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="eb962-129">備註</span><span class="sxs-lookup"><span data-stu-id="eb962-129">Remarks</span></span>

<span data-ttu-id="eb962-130">為數據表的每個資料行指定標頭。</span><span class="sxs-lookup"><span data-stu-id="eb962-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="eb962-131">資料行會以定義元素的順序顯示 `TableColumnHeader` 。</span><span class="sxs-lookup"><span data-stu-id="eb962-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="eb962-132">資料表必須有相同數目的 `TableColumnHeader` 元素做為專案 `TableRowEntry` 。</span><span class="sxs-lookup"><span data-stu-id="eb962-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="eb962-133">資料行標頭會定義如何顯示資料表頂端的文字。</span><span class="sxs-lookup"><span data-stu-id="eb962-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="eb962-134">資料列專案會定義要在資料表的資料列中顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="eb962-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="eb962-135">如需有關資料表視圖之元件的詳細資訊，請參閱[資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="eb962-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="eb962-136">範例</span><span class="sxs-lookup"><span data-stu-id="eb962-136">Example</span></span>

<span data-ttu-id="eb962-137">下列範例顯示兩個 `TableColumnHeader` 元素。</span><span class="sxs-lookup"><span data-stu-id="eb962-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="eb962-138">第一個元素定義的資料行的標籤為 "Column 1"，寬度為16個字元，而其標籤在左邊對齊。</span><span class="sxs-lookup"><span data-stu-id="eb962-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="eb962-139">第二個元素會定義其標籤為 "Column 2"、寬度為10個字元，且其標籤在資料行中央的資料行。</span><span class="sxs-lookup"><span data-stu-id="eb962-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="eb962-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb962-140">See Also</span></span>

[<span data-ttu-id="eb962-141">TableControl 之 TableColumnHeader 的對齊元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="eb962-141">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="eb962-142">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="eb962-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="eb962-143">TableControl 之 TableColumnHeader 的標籤元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="eb962-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="eb962-144">TableControl (格式的 TableHeaders 元素) </span><span class="sxs-lookup"><span data-stu-id="eb962-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="eb962-145">TableControl 元素的之 tablecolumnheader 寬度 (格式) </span><span class="sxs-lookup"><span data-stu-id="eb962-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="eb962-146">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="eb962-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
