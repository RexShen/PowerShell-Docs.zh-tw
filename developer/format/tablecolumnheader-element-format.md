---
title: TableColumnHeader 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063804"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="4675e-102">TableColumnHeader 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4675e-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="4675e-103">定義標籤，將資料行的寬度和資料表資料行的標籤對齊方式。</span><span class="sxs-lookup"><span data-stu-id="4675e-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="4675e-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableHeaders 項目 TableControl （格式） TableColumnHeader TableHeaders TableControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="4675e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4675e-105">語法</span><span class="sxs-lookup"><span data-stu-id="4675e-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4675e-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4675e-106">Attributes and Elements</span></span>

<span data-ttu-id="4675e-107">下列各節說明屬性、 子項目和父項目`TableColumnHeader`項目。</span><span class="sxs-lookup"><span data-stu-id="4675e-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4675e-108">屬性</span><span class="sxs-lookup"><span data-stu-id="4675e-108">Attributes</span></span>

<span data-ttu-id="4675e-109">無。</span><span class="sxs-lookup"><span data-stu-id="4675e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4675e-110">子元素</span><span class="sxs-lookup"><span data-stu-id="4675e-110">Child Elements</span></span>

|<span data-ttu-id="4675e-111">元素</span><span class="sxs-lookup"><span data-stu-id="4675e-111">Element</span></span>|<span data-ttu-id="4675e-112">描述</span><span class="sxs-lookup"><span data-stu-id="4675e-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4675e-113">TableControl （格式） 的 TableColumnHeader label 項目</span><span class="sxs-lookup"><span data-stu-id="4675e-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="4675e-114">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="4675e-114">Optional element.</span></span><br /><br /> <span data-ttu-id="4675e-115">定義顯示在資料行頂端的標籤。</span><span class="sxs-lookup"><span data-stu-id="4675e-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="4675e-116">如果未不指定任何標籤，會使用資料列中顯示其值之屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="4675e-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="4675e-117">TableControl （格式） 的 TableColumnHeader 的 width 元素</span><span class="sxs-lookup"><span data-stu-id="4675e-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="4675e-118">必要項目。</span><span class="sxs-lookup"><span data-stu-id="4675e-118">Required element.</span></span><br /><br /> <span data-ttu-id="4675e-119">指定的資料行的寬度 （以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="4675e-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="4675e-120">TableControl （格式） 的 TableColumnHeader 對齊項目</span><span class="sxs-lookup"><span data-stu-id="4675e-120">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="4675e-121">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="4675e-121">Optional element.</span></span><br /><br /> <span data-ttu-id="4675e-122">指定資料行的標籤顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="4675e-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="4675e-123">如果指定沒有對齊，則標籤會對齊左邊。</span><span class="sxs-lookup"><span data-stu-id="4675e-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4675e-124">父項目</span><span class="sxs-lookup"><span data-stu-id="4675e-124">Parent Elements</span></span>

|<span data-ttu-id="4675e-125">項目</span><span class="sxs-lookup"><span data-stu-id="4675e-125">Element</span></span>|<span data-ttu-id="4675e-126">描述</span><span class="sxs-lookup"><span data-stu-id="4675e-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4675e-127">TableHeaders 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="4675e-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="4675e-128">定義資料行的資料表檢視。</span><span class="sxs-lookup"><span data-stu-id="4675e-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4675e-129">備註</span><span class="sxs-lookup"><span data-stu-id="4675e-129">Remarks</span></span>

<span data-ttu-id="4675e-130">指定資料表的每個資料行的標頭。</span><span class="sxs-lookup"><span data-stu-id="4675e-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="4675e-131">資料行所顯示的順序在`TableColumnHeader`項目定義。</span><span class="sxs-lookup"><span data-stu-id="4675e-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="4675e-132">資料表必須有相同數目的`TableColumnHeader`項目與`TableRowEntry`項目。</span><span class="sxs-lookup"><span data-stu-id="4675e-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="4675e-133">資料行標頭會定義在資料表頂端的文字的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="4675e-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="4675e-134">資料列項目會定義哪些資料會顯示在資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="4675e-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="4675e-135">資料表檢視元件的相關資訊，請參閱[資料表檢視](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="4675e-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4675e-136">範例</span><span class="sxs-lookup"><span data-stu-id="4675e-136">Example</span></span>

<span data-ttu-id="4675e-137">下列範例示範兩個`TableColumnHeader`項目。</span><span class="sxs-lookup"><span data-stu-id="4675e-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="4675e-138">第一個項目會定義資料行，以及其標籤是 [資料行 1]，寬度為 16 個字元，其標籤會對齊左邊。</span><span class="sxs-lookup"><span data-stu-id="4675e-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="4675e-139">第二個元素會定義資料行，以及其標籤是 [資料行 2]，寬度為 10 個字元，其標籤會置中的資料行中。</span><span class="sxs-lookup"><span data-stu-id="4675e-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4675e-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4675e-140">See Also</span></span>

[<span data-ttu-id="4675e-141">TableControl （格式） 的 TableColumnHeader 對齊項目</span><span class="sxs-lookup"><span data-stu-id="4675e-141">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="4675e-142">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="4675e-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="4675e-143">TableControl （格式） 的 TableColumnHeader label 項目</span><span class="sxs-lookup"><span data-stu-id="4675e-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="4675e-144">TableHeaders TableControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="4675e-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="4675e-145">寬度 TableColumnHeader TableControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="4675e-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="4675e-146">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="4675e-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
