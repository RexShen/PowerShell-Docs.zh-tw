---
ms.date: 09/13/2016
ms.topic: reference
title: TableHeaders 元素 (格式)
description: TableHeaders 元素 (格式)
ms.openlocfilehash: 5ac4dccae746c167ebf95add9f3d18030a2b3a99
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659827"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="35571-103">TableHeaders 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="35571-103">TableHeaders Element (Format)</span></span>

<span data-ttu-id="35571-104">定義資料表之資料行的標頭。</span><span class="sxs-lookup"><span data-stu-id="35571-104">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="35571-105">ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) TableControl (格式的 TableHeaders 元素) </span><span class="sxs-lookup"><span data-stu-id="35571-105">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="35571-106">語法</span><span class="sxs-lookup"><span data-stu-id="35571-106">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="35571-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="35571-107">Attributes and Elements</span></span>

<span data-ttu-id="35571-108">下列各節描述專案的屬性、子項目和父元素 `TableHeaders` 。</span><span class="sxs-lookup"><span data-stu-id="35571-108">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="35571-109">要顯示之物件的每個屬性都必須要有一個子項目。</span><span class="sxs-lookup"><span data-stu-id="35571-109">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="35571-110">資料行標頭資訊會以指定子項目的順序顯示。</span><span class="sxs-lookup"><span data-stu-id="35571-110">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="35571-111">屬性</span><span class="sxs-lookup"><span data-stu-id="35571-111">Attributes</span></span>

<span data-ttu-id="35571-112">無。</span><span class="sxs-lookup"><span data-stu-id="35571-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="35571-113">子元素</span><span class="sxs-lookup"><span data-stu-id="35571-113">Child Elements</span></span>

|<span data-ttu-id="35571-114">元素</span><span class="sxs-lookup"><span data-stu-id="35571-114">Element</span></span>|<span data-ttu-id="35571-115">描述</span><span class="sxs-lookup"><span data-stu-id="35571-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="35571-116">TableColumnHeader 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="35571-116">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="35571-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="35571-117">Optional element.</span></span><br /><br /> <span data-ttu-id="35571-118">定義資料表視圖之資料行的標籤、寬度和對齊方式。</span><span class="sxs-lookup"><span data-stu-id="35571-118">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="35571-119">父項目</span><span class="sxs-lookup"><span data-stu-id="35571-119">Parent Elements</span></span>

|<span data-ttu-id="35571-120">元素</span><span class="sxs-lookup"><span data-stu-id="35571-120">Element</span></span>|<span data-ttu-id="35571-121">描述</span><span class="sxs-lookup"><span data-stu-id="35571-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="35571-122">TableControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="35571-122">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="35571-123">定義視圖的資料表格式。</span><span class="sxs-lookup"><span data-stu-id="35571-123">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="35571-124">備註</span><span class="sxs-lookup"><span data-stu-id="35571-124">Remarks</span></span>

<span data-ttu-id="35571-125">如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="35571-125">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="35571-126">範例</span><span class="sxs-lookup"><span data-stu-id="35571-126">Example</span></span>

<span data-ttu-id="35571-127">這個範例會顯示 `TableHeaders` 定義兩個數據行標頭的元素。</span><span class="sxs-lookup"><span data-stu-id="35571-127">This example shows a `TableHeaders` element that defines two column headers.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="35571-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35571-128">See Also</span></span>

[<span data-ttu-id="35571-129">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="35571-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="35571-130">TableColumnHeader 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="35571-130">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="35571-131">TableControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="35571-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="35571-132">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="35571-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
