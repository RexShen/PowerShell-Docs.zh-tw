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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361797"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a><span data-ttu-id="f0ec8-102">TableControl 之 TableRowEntries 的 TableRowEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="f0ec8-102">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

<span data-ttu-id="f0ec8-103">定義在資料表的資料列中顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="f0ec8-103">Defines the data that is displayed in a row of the table.</span></span>

<span data-ttu-id="f0ec8-104">TableRowEntry for TableRowEntries 之 TableControl （Format） TableControl 元素的 Configuration 元素（格式） ViewDefinitions 元素（格式） TableRowEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f0ec8-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f0ec8-105">語法</span><span class="sxs-lookup"><span data-stu-id="f0ec8-105">Syntax</span></span>

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f0ec8-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="f0ec8-106">Attributes and Elements</span></span>

<span data-ttu-id="f0ec8-107">下列各節描述 `TableRowEntry` 元素的屬性、子專案和父項目。</span><span class="sxs-lookup"><span data-stu-id="f0ec8-107">The following sections describe attributes, child elements, and parent element of the `TableRowEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f0ec8-108">屬性</span><span class="sxs-lookup"><span data-stu-id="f0ec8-108">Attributes</span></span>

<span data-ttu-id="f0ec8-109">無。</span><span class="sxs-lookup"><span data-stu-id="f0ec8-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f0ec8-110">子元素</span><span class="sxs-lookup"><span data-stu-id="f0ec8-110">Child Elements</span></span>

|<span data-ttu-id="f0ec8-111">項目</span><span class="sxs-lookup"><span data-stu-id="f0ec8-111">Element</span></span>|<span data-ttu-id="f0ec8-112">說明</span><span class="sxs-lookup"><span data-stu-id="f0ec8-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f0ec8-113">TableControl 之 TableRowEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f0ec8-113">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="f0ec8-114">必要元素。</span><span class="sxs-lookup"><span data-stu-id="f0ec8-114">Required element.</span></span><br /><br /> <span data-ttu-id="f0ec8-115">定義物件，其屬性值會顯示在資料列中。</span><span class="sxs-lookup"><span data-stu-id="f0ec8-115">Defines the objects whose property values are displayed in the row.</span></span>|
|[<span data-ttu-id="f0ec8-116">TableControl 之 TableRowEntry 的 TableColumnItems 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f0ec8-116">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="f0ec8-117">必要元素。</span><span class="sxs-lookup"><span data-stu-id="f0ec8-117">Required element.</span></span><br /><br /> <span data-ttu-id="f0ec8-118">定義要顯示其值的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="f0ec8-118">Defines the properties or scripts whose values are displayed.</span></span>|
|[<span data-ttu-id="f0ec8-119">TableControl 的 TableRowEntry 的 Wrap 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f0ec8-119">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="f0ec8-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f0ec8-120">Optional element.</span></span><br /><br /> <span data-ttu-id="f0ec8-121">指定超過欄寬度的文字會顯示在下一行。</span><span class="sxs-lookup"><span data-stu-id="f0ec8-121">Specifies that text that exceeds the column width is displayed on the next line.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f0ec8-122">父元素</span><span class="sxs-lookup"><span data-stu-id="f0ec8-122">Parent Elements</span></span>

|<span data-ttu-id="f0ec8-123">項目</span><span class="sxs-lookup"><span data-stu-id="f0ec8-123">Element</span></span>|<span data-ttu-id="f0ec8-124">說明</span><span class="sxs-lookup"><span data-stu-id="f0ec8-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f0ec8-125">TableControl 的 TableRowEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f0ec8-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="f0ec8-126">定義資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="f0ec8-126">Defines the rows of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f0ec8-127">備註</span><span class="sxs-lookup"><span data-stu-id="f0ec8-127">Remarks</span></span>

<span data-ttu-id="f0ec8-128">必須指定一個 `TableColumnItems` 元素和一個 `EntrySelectedBy` 元素。</span><span class="sxs-lookup"><span data-stu-id="f0ec8-128">One `TableColumnItems` element and one `EntrySelectedBy` element must be specified.</span></span>

<span data-ttu-id="f0ec8-129">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="f0ec8-129">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f0ec8-130">範例</span><span class="sxs-lookup"><span data-stu-id="f0ec8-130">Example</span></span>

<span data-ttu-id="f0ec8-131">下列範例顯示的 `TableRowEntry` 專案會定義一個資料列，以顯示 system.servicemodel 物件的兩個屬性[值。](/dotnet/api/System.Diagnostics.Process)</span><span class="sxs-lookup"><span data-stu-id="f0ec8-131">The following example shows a `TableRowEntry` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f0ec8-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0ec8-132">See Also</span></span>

[<span data-ttu-id="f0ec8-133">建立資料表視圖</span><span class="sxs-lookup"><span data-stu-id="f0ec8-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f0ec8-134">TableControl 之 TableRowEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f0ec8-134">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="f0ec8-135">TableControl 之 TableRowEntry 的 TableColumnItems 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f0ec8-135">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="f0ec8-136">TableControl 的 TableRowEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f0ec8-136">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="f0ec8-137">TableControl 的 TableRowEntry 的 Wrap 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f0ec8-137">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="f0ec8-138">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="f0ec8-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
