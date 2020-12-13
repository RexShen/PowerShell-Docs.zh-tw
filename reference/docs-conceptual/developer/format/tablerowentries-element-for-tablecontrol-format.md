---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 的 TableRowEntries 元素 (格式)
description: TableControl 的 TableRowEntries 元素 (格式)
ms.openlocfilehash: 1df63e645234da8276c7ccc5af34e81a56475e43
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651469"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="dc3cc-103">TableControl 的 TableRowEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dc3cc-103">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="dc3cc-104">定義資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="dc3cc-104">Defines the rows of the table.</span></span>

<span data-ttu-id="dc3cc-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) TableControl 元素 (格式) TableControl (格式的 TableRowEntries 元素) </span><span class="sxs-lookup"><span data-stu-id="dc3cc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dc3cc-106">語法</span><span class="sxs-lookup"><span data-stu-id="dc3cc-106">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dc3cc-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dc3cc-107">Attributes and Elements</span></span>

<span data-ttu-id="dc3cc-108">下列各節描述專案的屬性、子項目和父元素 `TableRowEntries` 。</span><span class="sxs-lookup"><span data-stu-id="dc3cc-108">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dc3cc-109">屬性</span><span class="sxs-lookup"><span data-stu-id="dc3cc-109">Attributes</span></span>

<span data-ttu-id="dc3cc-110">無。</span><span class="sxs-lookup"><span data-stu-id="dc3cc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dc3cc-111">子元素</span><span class="sxs-lookup"><span data-stu-id="dc3cc-111">Child Elements</span></span>

|<span data-ttu-id="dc3cc-112">元素</span><span class="sxs-lookup"><span data-stu-id="dc3cc-112">Element</span></span>|<span data-ttu-id="dc3cc-113">描述</span><span class="sxs-lookup"><span data-stu-id="dc3cc-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dc3cc-114">TableControl 之 TableRowEntries 的 TableRowEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dc3cc-114">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="dc3cc-115">必要元素。</span><span class="sxs-lookup"><span data-stu-id="dc3cc-115">Required element.</span></span><br /><br /> <span data-ttu-id="dc3cc-116">定義顯示在資料表資料列中的資料。</span><span class="sxs-lookup"><span data-stu-id="dc3cc-116">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dc3cc-117">父項目</span><span class="sxs-lookup"><span data-stu-id="dc3cc-117">Parent Elements</span></span>

|<span data-ttu-id="dc3cc-118">元素</span><span class="sxs-lookup"><span data-stu-id="dc3cc-118">Element</span></span>|<span data-ttu-id="dc3cc-119">描述</span><span class="sxs-lookup"><span data-stu-id="dc3cc-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dc3cc-120">TableControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dc3cc-120">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="dc3cc-121">定義視圖的資料表格式。</span><span class="sxs-lookup"><span data-stu-id="dc3cc-121">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dc3cc-122">備註</span><span class="sxs-lookup"><span data-stu-id="dc3cc-122">Remarks</span></span>

<span data-ttu-id="dc3cc-123">您必須為數據表視圖指定一個或多個 `TableRowEntry` 元素。</span><span class="sxs-lookup"><span data-stu-id="dc3cc-123">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="dc3cc-124">可以加入的專案數目沒有最大限制，也不會影響 `TableRowEntry` 其順序。</span><span class="sxs-lookup"><span data-stu-id="dc3cc-124">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="dc3cc-125">如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="dc3cc-125">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="dc3cc-126">範例</span><span class="sxs-lookup"><span data-stu-id="dc3cc-126">Example</span></span>

<span data-ttu-id="dc3cc-127">下列範例顯示的專案 `TableRowEntries` 會定義一個資料列，該資料列會顯示 system.string 物件之[](/dotnet/api/System.Diagnostics.Process)兩個屬性的值。</span><span class="sxs-lookup"><span data-stu-id="dc3cc-127">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntries>
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
</TableRowEntries>

```

## <a name="see-also"></a><span data-ttu-id="dc3cc-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc3cc-128">See Also</span></span>

[<span data-ttu-id="dc3cc-129">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="dc3cc-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="dc3cc-130">TableControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dc3cc-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="dc3cc-131">TableRowEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="dc3cc-131">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="dc3cc-132">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="dc3cc-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
