---
title: TableControl 之 TableRowEntries 的 TableRowEntry 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361797"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a><span data-ttu-id="4688b-102">TableControl 之 TableRowEntries 的 TableRowEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4688b-102">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

<span data-ttu-id="4688b-103">定義在資料表的資料列中顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="4688b-103">Defines the data that is displayed in a row of the table.</span></span>

<span data-ttu-id="4688b-104">TableRowEntry for TableRowEntries 之 TableControl （Format） TableControl 元素的 Configuration 元素（格式） ViewDefinitions 元素（格式） TableRowEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4688b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4688b-105">語法</span><span class="sxs-lookup"><span data-stu-id="4688b-105">Syntax</span></span>

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4688b-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="4688b-106">Attributes and Elements</span></span>

<span data-ttu-id="4688b-107">下列各節描述 `TableRowEntry` 元素的屬性、子專案和父項目。</span><span class="sxs-lookup"><span data-stu-id="4688b-107">The following sections describe attributes, child elements, and parent element of the `TableRowEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4688b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="4688b-108">Attributes</span></span>

<span data-ttu-id="4688b-109">無。</span><span class="sxs-lookup"><span data-stu-id="4688b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4688b-110">子元素</span><span class="sxs-lookup"><span data-stu-id="4688b-110">Child Elements</span></span>

|<span data-ttu-id="4688b-111">元素</span><span class="sxs-lookup"><span data-stu-id="4688b-111">Element</span></span>|<span data-ttu-id="4688b-112">描述</span><span class="sxs-lookup"><span data-stu-id="4688b-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4688b-113">TableControl 之 TableRowEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4688b-113">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="4688b-114">必要項目。</span><span class="sxs-lookup"><span data-stu-id="4688b-114">Required element.</span></span><br /><br /> <span data-ttu-id="4688b-115">定義物件，其屬性值會顯示在資料列中。</span><span class="sxs-lookup"><span data-stu-id="4688b-115">Defines the objects whose property values are displayed in the row.</span></span>|
|[<span data-ttu-id="4688b-116">TableControl 之 TableRowEntry 的 TableColumnItems 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4688b-116">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="4688b-117">必要項目。</span><span class="sxs-lookup"><span data-stu-id="4688b-117">Required element.</span></span><br /><br /> <span data-ttu-id="4688b-118">定義要顯示其值的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="4688b-118">Defines the properties or scripts whose values are displayed.</span></span>|
|[<span data-ttu-id="4688b-119">TableControl 的 TableRowEntry 的 Wrap 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4688b-119">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="4688b-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="4688b-120">Optional element.</span></span><br /><br /> <span data-ttu-id="4688b-121">指定超過欄寬度的文字會顯示在下一行。</span><span class="sxs-lookup"><span data-stu-id="4688b-121">Specifies that text that exceeds the column width is displayed on the next line.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4688b-122">父元素</span><span class="sxs-lookup"><span data-stu-id="4688b-122">Parent Elements</span></span>

|<span data-ttu-id="4688b-123">元素</span><span class="sxs-lookup"><span data-stu-id="4688b-123">Element</span></span>|<span data-ttu-id="4688b-124">描述</span><span class="sxs-lookup"><span data-stu-id="4688b-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4688b-125">TableControl 的 TableRowEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4688b-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="4688b-126">定義資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="4688b-126">Defines the rows of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4688b-127">備註</span><span class="sxs-lookup"><span data-stu-id="4688b-127">Remarks</span></span>

<span data-ttu-id="4688b-128">必須指定一個 `TableColumnItems` 元素和一個 `EntrySelectedBy` 元素。</span><span class="sxs-lookup"><span data-stu-id="4688b-128">One `TableColumnItems` element and one `EntrySelectedBy` element must be specified.</span></span>

<span data-ttu-id="4688b-129">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="4688b-129">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4688b-130">範例</span><span class="sxs-lookup"><span data-stu-id="4688b-130">Example</span></span>

<span data-ttu-id="4688b-131">下列範例顯示的 `TableRowEntry` 專案會定義一個資料列，以顯示 system.servicemodel 物件的兩個屬性[值。](/dotnet/api/System.Diagnostics.Process)</span><span class="sxs-lookup"><span data-stu-id="4688b-131">The following example shows a `TableRowEntry` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4688b-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4688b-132">See Also</span></span>

[<span data-ttu-id="4688b-133">建立資料表視圖</span><span class="sxs-lookup"><span data-stu-id="4688b-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="4688b-134">TableControl 之 TableRowEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4688b-134">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="4688b-135">TableControl 之 TableRowEntry 的 TableColumnItems 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4688b-135">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="4688b-136">TableControl 的 TableRowEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4688b-136">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="4688b-137">TableControl 的 TableRowEntry 的 Wrap 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4688b-137">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="4688b-138">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="4688b-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
