---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 TableRowEntries 的 TableRowEntry 元素 (格式)
description: TableControl 之 TableRowEntries 的 TableRowEntry 元素 (格式)
ms.openlocfilehash: 60d64b7c14b40e87825ada36e19f52a66fe8b6cb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659762"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a><span data-ttu-id="2ab5c-103">TableControl 之 TableRowEntries 的 TableRowEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2ab5c-103">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

<span data-ttu-id="2ab5c-104">定義顯示在資料表資料列中的資料。</span><span class="sxs-lookup"><span data-stu-id="2ab5c-104">Defines the data that is displayed in a row of the table.</span></span>

<span data-ttu-id="2ab5c-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) TableControl 元素 (format) TableRowEntries 元素 for TableControl (Format) TableRowEntry 元素 for TableRowEntries for TableControl (格式) </span><span class="sxs-lookup"><span data-stu-id="2ab5c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2ab5c-106">語法</span><span class="sxs-lookup"><span data-stu-id="2ab5c-106">Syntax</span></span>

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2ab5c-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2ab5c-107">Attributes and Elements</span></span>

<span data-ttu-id="2ab5c-108">下列各節描述專案的屬性、子項目和父元素 `TableRowEntry` 。</span><span class="sxs-lookup"><span data-stu-id="2ab5c-108">The following sections describe attributes, child elements, and parent element of the `TableRowEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2ab5c-109">屬性</span><span class="sxs-lookup"><span data-stu-id="2ab5c-109">Attributes</span></span>

<span data-ttu-id="2ab5c-110">無。</span><span class="sxs-lookup"><span data-stu-id="2ab5c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2ab5c-111">子元素</span><span class="sxs-lookup"><span data-stu-id="2ab5c-111">Child Elements</span></span>

|<span data-ttu-id="2ab5c-112">元素</span><span class="sxs-lookup"><span data-stu-id="2ab5c-112">Element</span></span>|<span data-ttu-id="2ab5c-113">描述</span><span class="sxs-lookup"><span data-stu-id="2ab5c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2ab5c-114">適用于 TableRowEntry 的 TableControl (格式的之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="2ab5c-114">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="2ab5c-115">必要元素。</span><span class="sxs-lookup"><span data-stu-id="2ab5c-115">Required element.</span></span><br /><br /> <span data-ttu-id="2ab5c-116">定義其屬性值會顯示在資料列中的物件。</span><span class="sxs-lookup"><span data-stu-id="2ab5c-116">Defines the objects whose property values are displayed in the row.</span></span>|
|[<span data-ttu-id="2ab5c-117">TableControl 之 TableRowEntry 的 TableColumnItems 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2ab5c-117">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="2ab5c-118">必要元素。</span><span class="sxs-lookup"><span data-stu-id="2ab5c-118">Required element.</span></span><br /><br /> <span data-ttu-id="2ab5c-119">定義顯示其值的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="2ab5c-119">Defines the properties or scripts whose values are displayed.</span></span>|
|[<span data-ttu-id="2ab5c-120">適用于 TableControl (格式的 TableRowEntry Wrap 元素) </span><span class="sxs-lookup"><span data-stu-id="2ab5c-120">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="2ab5c-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="2ab5c-121">Optional element.</span></span><br /><br /> <span data-ttu-id="2ab5c-122">指定在下一行顯示超過欄寬度的文字。</span><span class="sxs-lookup"><span data-stu-id="2ab5c-122">Specifies that text that exceeds the column width is displayed on the next line.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2ab5c-123">父項目</span><span class="sxs-lookup"><span data-stu-id="2ab5c-123">Parent Elements</span></span>

|<span data-ttu-id="2ab5c-124">元素</span><span class="sxs-lookup"><span data-stu-id="2ab5c-124">Element</span></span>|<span data-ttu-id="2ab5c-125">描述</span><span class="sxs-lookup"><span data-stu-id="2ab5c-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2ab5c-126">TableControl 的 TableRowEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2ab5c-126">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="2ab5c-127">定義資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="2ab5c-127">Defines the rows of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2ab5c-128">備註</span><span class="sxs-lookup"><span data-stu-id="2ab5c-128">Remarks</span></span>

<span data-ttu-id="2ab5c-129">`TableColumnItems`必須指定一個元素和一個 `EntrySelectedBy` 元素。</span><span class="sxs-lookup"><span data-stu-id="2ab5c-129">One `TableColumnItems` element and one `EntrySelectedBy` element must be specified.</span></span>

<span data-ttu-id="2ab5c-130">如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="2ab5c-130">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2ab5c-131">範例</span><span class="sxs-lookup"><span data-stu-id="2ab5c-131">Example</span></span>

<span data-ttu-id="2ab5c-132">下列範例顯示的專案 `TableRowEntry` 會定義一個資料列，該資料列會顯示 system.string 物件之[](/dotnet/api/System.Diagnostics.Process)兩個屬性的值。</span><span class="sxs-lookup"><span data-stu-id="2ab5c-132">The following example shows a `TableRowEntry` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName> Property for first column</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName> Property for second column</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a><span data-ttu-id="2ab5c-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ab5c-133">See Also</span></span>

[<span data-ttu-id="2ab5c-134">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="2ab5c-134">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2ab5c-135">適用于 TableRowEntry 的 TableControl (格式的之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="2ab5c-135">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="2ab5c-136">TableControl 之 TableRowEntry 的 TableColumnItems 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2ab5c-136">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="2ab5c-137">TableControl 的 TableRowEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2ab5c-137">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="2ab5c-138">適用于 TableControl (格式的 TableRowEntry Wrap 元素) </span><span class="sxs-lookup"><span data-stu-id="2ab5c-138">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="2ab5c-139">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="2ab5c-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
