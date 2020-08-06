---
title: TableControl (格式) 的 TableRowEntry 的 TableColumnItems 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 661b938e8db0e68e10dc05f552e4f3a14608bc55
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785144"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="cea20-102">TableControl 之 TableRowEntry 的 TableColumnItems 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="cea20-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="cea20-103">定義屬性或腳本，其值會顯示在資料列中。</span><span class="sxs-lookup"><span data-stu-id="cea20-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="cea20-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 專案 (格式) TableControl (格式) TableRowEntry 元素，TableRowEntries 的 TableControl (格式) TableColumnItems 元素 (</span><span class="sxs-lookup"><span data-stu-id="cea20-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cea20-105">語法</span><span class="sxs-lookup"><span data-stu-id="cea20-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cea20-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cea20-106">Attributes and Elements</span></span>

<span data-ttu-id="cea20-107">下列各節描述元素的屬性、子專案和父項目 `TableColumnItems` 。</span><span class="sxs-lookup"><span data-stu-id="cea20-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cea20-108">屬性</span><span class="sxs-lookup"><span data-stu-id="cea20-108">Attributes</span></span>

<span data-ttu-id="cea20-109">無。</span><span class="sxs-lookup"><span data-stu-id="cea20-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cea20-110">子元素</span><span class="sxs-lookup"><span data-stu-id="cea20-110">Child Elements</span></span>

|<span data-ttu-id="cea20-111">元素</span><span class="sxs-lookup"><span data-stu-id="cea20-111">Element</span></span>|<span data-ttu-id="cea20-112">描述</span><span class="sxs-lookup"><span data-stu-id="cea20-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cea20-113">TableControl 之 TableColumnItems 的 TableColumnItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="cea20-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="cea20-114">必要元素。</span><span class="sxs-lookup"><span data-stu-id="cea20-114">Required element.</span></span><br /><br /> <span data-ttu-id="cea20-115">定義屬性或腳本，其值會顯示在資料列的資料行中。</span><span class="sxs-lookup"><span data-stu-id="cea20-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cea20-116">父項目</span><span class="sxs-lookup"><span data-stu-id="cea20-116">Parent Elements</span></span>

|<span data-ttu-id="cea20-117">元素</span><span class="sxs-lookup"><span data-stu-id="cea20-117">Element</span></span>|<span data-ttu-id="cea20-118">描述</span><span class="sxs-lookup"><span data-stu-id="cea20-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cea20-119">TableControl 之 TableRowEntries 的 TableRowEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="cea20-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="cea20-120">定義在資料表的資料列中顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="cea20-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cea20-121">備註</span><span class="sxs-lookup"><span data-stu-id="cea20-121">Remarks</span></span>

<span data-ttu-id="cea20-122">資料 `TableColumnItem` 列的每個資料行都需要一個元素。</span><span class="sxs-lookup"><span data-stu-id="cea20-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="cea20-123">第一個專案會顯示在第一個資料行、第二個數據行中的第二個專案，依此類推。</span><span class="sxs-lookup"><span data-stu-id="cea20-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="cea20-124">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="cea20-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="cea20-125">範例</span><span class="sxs-lookup"><span data-stu-id="cea20-125">Example</span></span>

<span data-ttu-id="cea20-126">下列範例顯示的 `TableColumnItems` 元素會定義一個 system.servicemodel 物件的三[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)個屬性。</span><span class="sxs-lookup"><span data-stu-id="cea20-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cea20-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cea20-127">See Also</span></span>

[<span data-ttu-id="cea20-128">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="cea20-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="cea20-129">之 tablecolumnitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="cea20-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="cea20-130">TableRowEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="cea20-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="cea20-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="cea20-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
