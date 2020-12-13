---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 TableRowEntry 的 TableColumnItems 元素 (格式)
description: TableControl 之 TableRowEntry 的 TableColumnItems 元素 (格式)
ms.openlocfilehash: 4d600a366d2be1c453f05b301bdf575351dd51c1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667754"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="961e8-103">TableControl 之 TableRowEntry 的 TableColumnItems 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="961e8-103">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="961e8-104">定義其值會顯示在資料列中的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="961e8-104">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="961e8-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) TableControl 元素 (format) TableRowEntries 元素 for TableControl (Format) TableRowEntry TableRowEntries for TableControl for TableColumnItems (TableControlEntry for TableControl for) format (</span><span class="sxs-lookup"><span data-stu-id="961e8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="961e8-106">語法</span><span class="sxs-lookup"><span data-stu-id="961e8-106">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="961e8-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="961e8-107">Attributes and Elements</span></span>

<span data-ttu-id="961e8-108">下列各節描述專案的屬性、子項目和父元素 `TableColumnItems` 。</span><span class="sxs-lookup"><span data-stu-id="961e8-108">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="961e8-109">屬性</span><span class="sxs-lookup"><span data-stu-id="961e8-109">Attributes</span></span>

<span data-ttu-id="961e8-110">無。</span><span class="sxs-lookup"><span data-stu-id="961e8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="961e8-111">子元素</span><span class="sxs-lookup"><span data-stu-id="961e8-111">Child Elements</span></span>

|<span data-ttu-id="961e8-112">元素</span><span class="sxs-lookup"><span data-stu-id="961e8-112">Element</span></span>|<span data-ttu-id="961e8-113">描述</span><span class="sxs-lookup"><span data-stu-id="961e8-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="961e8-114">TableControl 之 TableColumnItems 的 TableColumnItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="961e8-114">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="961e8-115">必要元素。</span><span class="sxs-lookup"><span data-stu-id="961e8-115">Required element.</span></span><br /><br /> <span data-ttu-id="961e8-116">定義其值會顯示在資料列的資料行中的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="961e8-116">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="961e8-117">父項目</span><span class="sxs-lookup"><span data-stu-id="961e8-117">Parent Elements</span></span>

|<span data-ttu-id="961e8-118">元素</span><span class="sxs-lookup"><span data-stu-id="961e8-118">Element</span></span>|<span data-ttu-id="961e8-119">描述</span><span class="sxs-lookup"><span data-stu-id="961e8-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="961e8-120">TableControl 之 TableRowEntries 的 TableRowEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="961e8-120">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="961e8-121">定義顯示在資料表資料列中的資料。</span><span class="sxs-lookup"><span data-stu-id="961e8-121">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="961e8-122">備註</span><span class="sxs-lookup"><span data-stu-id="961e8-122">Remarks</span></span>

<span data-ttu-id="961e8-123">資料 `TableColumnItem` 列的每個資料行都需要元素。</span><span class="sxs-lookup"><span data-stu-id="961e8-123">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="961e8-124">第一個專案會顯示在第一個資料行中，第二個數據行中的第二個專案，依此類推。</span><span class="sxs-lookup"><span data-stu-id="961e8-124">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="961e8-125">如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="961e8-125">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="961e8-126">範例</span><span class="sxs-lookup"><span data-stu-id="961e8-126">Example</span></span>

<span data-ttu-id="961e8-127">下列範例顯示的專案 `TableColumnItems` 會定義每個 system.string 物件的[](/dotnet/api/System.Diagnostics.Process)三個屬性。</span><span class="sxs-lookup"><span data-stu-id="961e8-127">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a><span data-ttu-id="961e8-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="961e8-128">See Also</span></span>

[<span data-ttu-id="961e8-129">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="961e8-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="961e8-130">之 tablecolumnitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="961e8-130">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="961e8-131">TableRowEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="961e8-131">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="961e8-132">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="961e8-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
