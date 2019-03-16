---
title: TableControl （格式） 的 TableRowEntries TableRowEntry 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2019
ms.locfileid: "58059873"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a><span data-ttu-id="18e04-102">TableControl （格式） 的 TableRowEntries TableRowEntry 項目</span><span class="sxs-lookup"><span data-stu-id="18e04-102">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

<span data-ttu-id="18e04-103">定義會顯示在資料表資料列的資料。</span><span class="sxs-lookup"><span data-stu-id="18e04-103">Defines the data that is displayed in a row of the table.</span></span>

<span data-ttu-id="18e04-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 TableControl （格式） TableRowEntry TableRowEntries TableControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="18e04-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="18e04-105">語法</span><span class="sxs-lookup"><span data-stu-id="18e04-105">Syntax</span></span>

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="18e04-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="18e04-106">Attributes and Elements</span></span>

<span data-ttu-id="18e04-107">下列各節說明屬性、 子項目和父項目`TableRowEntry`項目。</span><span class="sxs-lookup"><span data-stu-id="18e04-107">The following sections describe attributes, child elements, and parent element of the `TableRowEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="18e04-108">屬性</span><span class="sxs-lookup"><span data-stu-id="18e04-108">Attributes</span></span>

<span data-ttu-id="18e04-109">無。</span><span class="sxs-lookup"><span data-stu-id="18e04-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="18e04-110">子元素</span><span class="sxs-lookup"><span data-stu-id="18e04-110">Child Elements</span></span>

|<span data-ttu-id="18e04-111">元素</span><span class="sxs-lookup"><span data-stu-id="18e04-111">Element</span></span>|<span data-ttu-id="18e04-112">描述</span><span class="sxs-lookup"><span data-stu-id="18e04-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="18e04-113">TableControl （格式） 的 TableRowEntry EntrySelectedBy 項目</span><span class="sxs-lookup"><span data-stu-id="18e04-113">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="18e04-114">必要項目。</span><span class="sxs-lookup"><span data-stu-id="18e04-114">Required element.</span></span><br /><br /> <span data-ttu-id="18e04-115">定義其屬性值會顯示資料列中的物件。</span><span class="sxs-lookup"><span data-stu-id="18e04-115">Defines the objects whose property values are displayed in the row.</span></span>|
|[<span data-ttu-id="18e04-116">TableControl （格式） 的 TableRowEntry TableColumnItems 項目</span><span class="sxs-lookup"><span data-stu-id="18e04-116">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="18e04-117">必要項目。</span><span class="sxs-lookup"><span data-stu-id="18e04-117">Required element.</span></span><br /><br /> <span data-ttu-id="18e04-118">定義屬性或其值會顯示指令碼。</span><span class="sxs-lookup"><span data-stu-id="18e04-118">Defines the properties or scripts whose values are displayed.</span></span>|
|[<span data-ttu-id="18e04-119">如 TableRowEntry 包裝項目，如 TableControl （格式）</span><span class="sxs-lookup"><span data-stu-id="18e04-119">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="18e04-120">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="18e04-120">Optional element.</span></span><br /><br /> <span data-ttu-id="18e04-121">指定超過欄寬度的文字會顯示在下一行。</span><span class="sxs-lookup"><span data-stu-id="18e04-121">Specifies that text that exceeds the column width is displayed on the next line.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="18e04-122">父元素</span><span class="sxs-lookup"><span data-stu-id="18e04-122">Parent Elements</span></span>

|<span data-ttu-id="18e04-123">元素</span><span class="sxs-lookup"><span data-stu-id="18e04-123">Element</span></span>|<span data-ttu-id="18e04-124">描述</span><span class="sxs-lookup"><span data-stu-id="18e04-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="18e04-125">TableRowEntries TableControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="18e04-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="18e04-126">定義資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="18e04-126">Defines the rows of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="18e04-127">備註</span><span class="sxs-lookup"><span data-stu-id="18e04-127">Remarks</span></span>

<span data-ttu-id="18e04-128">一`TableColumnItems`項目和一個`EntrySelectedBy`必須指定項目。</span><span class="sxs-lookup"><span data-stu-id="18e04-128">One `TableColumnItems` element and one `EntrySelectedBy` element must be specified.</span></span>

<span data-ttu-id="18e04-129">資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="18e04-129">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="18e04-130">範例</span><span class="sxs-lookup"><span data-stu-id="18e04-130">Example</span></span>

<span data-ttu-id="18e04-131">下列範例所示`TableRowEntry`項目，定義會顯示兩個屬性的值的資料列[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件。</span><span class="sxs-lookup"><span data-stu-id="18e04-131">The following example shows a `TableRowEntry` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="18e04-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18e04-132">See Also</span></span>

[<span data-ttu-id="18e04-133">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="18e04-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="18e04-134">TableControl （格式） 的 TableRowEntry EntrySelectedBy 項目</span><span class="sxs-lookup"><span data-stu-id="18e04-134">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="18e04-135">TableControl （格式） 的 TableRowEntry TableColumnItems 項目</span><span class="sxs-lookup"><span data-stu-id="18e04-135">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="18e04-136">TableRowEntries TableControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="18e04-136">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="18e04-137">如 TableRowEntry 包裝項目，如 TableControl （格式）</span><span class="sxs-lookup"><span data-stu-id="18e04-137">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="18e04-138">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="18e04-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
