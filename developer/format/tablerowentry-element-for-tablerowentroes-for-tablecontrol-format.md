---
title: TableControl （格式） 的 TableRowEntroes TableRowEntry 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 001d46debde61f928c338b2f68112fb201f96216
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853584"
---
# <a name="tablerowentry-element-for-tablerowentroes-for-tablecontrol-format"></a><span data-ttu-id="687d0-102">TableControl 之 TableRowEntroes 的 TableRowEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="687d0-102">TableRowEntry Element for TableRowEntroes for TableControl (Format)</span></span>

<span data-ttu-id="687d0-103">定義會顯示在資料表資料列的資料。</span><span class="sxs-lookup"><span data-stu-id="687d0-103">Defines the data that is displayed in a row of the table.</span></span>

<span data-ttu-id="687d0-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 TableControl （格式） TableRowEntry TableRowEntries TableControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="687d0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="687d0-105">語法</span><span class="sxs-lookup"><span data-stu-id="687d0-105">Syntax</span></span>

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="687d0-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="687d0-106">Attributes and Elements</span></span>

<span data-ttu-id="687d0-107">下列各節說明屬性、 子項目和父項目`TableRowEntry`項目。</span><span class="sxs-lookup"><span data-stu-id="687d0-107">The following sections describe attributes, child elements, and parent element of the `TableRowEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="687d0-108">屬性</span><span class="sxs-lookup"><span data-stu-id="687d0-108">Attributes</span></span>

<span data-ttu-id="687d0-109">無。</span><span class="sxs-lookup"><span data-stu-id="687d0-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="687d0-110">子元素</span><span class="sxs-lookup"><span data-stu-id="687d0-110">Child Elements</span></span>

|<span data-ttu-id="687d0-111">元素</span><span class="sxs-lookup"><span data-stu-id="687d0-111">Element</span></span>|<span data-ttu-id="687d0-112">描述</span><span class="sxs-lookup"><span data-stu-id="687d0-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="687d0-113">TableControl （格式） 的 TableRowEntry EntrySelectedBy 項目</span><span class="sxs-lookup"><span data-stu-id="687d0-113">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="687d0-114">必要項目。</span><span class="sxs-lookup"><span data-stu-id="687d0-114">Required element.</span></span><br /><br /> <span data-ttu-id="687d0-115">定義其屬性值會顯示資料列中的物件。</span><span class="sxs-lookup"><span data-stu-id="687d0-115">Defines the objects whose property values are displayed in the row.</span></span>|
|[<span data-ttu-id="687d0-116">TableControl （格式） 的 TableRowEntry TableColumnItems 項目</span><span class="sxs-lookup"><span data-stu-id="687d0-116">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="687d0-117">必要項目。</span><span class="sxs-lookup"><span data-stu-id="687d0-117">Required element.</span></span><br /><br /> <span data-ttu-id="687d0-118">定義屬性或其值會顯示指令碼。</span><span class="sxs-lookup"><span data-stu-id="687d0-118">Defines the properties or scripts whose values are displayed.</span></span>|
|[<span data-ttu-id="687d0-119">如 TableRowEntry 包裝項目，如 TableCntrol （格式）</span><span class="sxs-lookup"><span data-stu-id="687d0-119">Wrap Element for TableRowEntry for TableCntrol (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrl-format.md)|<span data-ttu-id="687d0-120">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="687d0-120">Optional element.</span></span><br /><br /> <span data-ttu-id="687d0-121">指定超過欄寬度的文字會顯示在下一行。</span><span class="sxs-lookup"><span data-stu-id="687d0-121">Specifies that text that exceeds the column width is displayed on the next line.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="687d0-122">父元素</span><span class="sxs-lookup"><span data-stu-id="687d0-122">Parent Elements</span></span>

|<span data-ttu-id="687d0-123">元素</span><span class="sxs-lookup"><span data-stu-id="687d0-123">Element</span></span>|<span data-ttu-id="687d0-124">描述</span><span class="sxs-lookup"><span data-stu-id="687d0-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="687d0-125">TableRowEntries TableControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="687d0-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="687d0-126">定義資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="687d0-126">Defines the rows of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="687d0-127">備註</span><span class="sxs-lookup"><span data-stu-id="687d0-127">Remarks</span></span>

<span data-ttu-id="687d0-128">一`TableColumnItems`項目和一個`EntrySelectedBy`必須指定項目。</span><span class="sxs-lookup"><span data-stu-id="687d0-128">One `TableColumnItems` element and one `EntrySelectedBy` element must be specified.</span></span>

<span data-ttu-id="687d0-129">資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="687d0-129">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="687d0-130">範例</span><span class="sxs-lookup"><span data-stu-id="687d0-130">Example</span></span>

<span data-ttu-id="687d0-131">下列範例所示`TableRowEntry`項目，定義會顯示兩個屬性的值的資料列[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件。</span><span class="sxs-lookup"><span data-stu-id="687d0-131">The following example shows a `TableRowEntry` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="687d0-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="687d0-132">See Also</span></span>

[<span data-ttu-id="687d0-133">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="687d0-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="687d0-134">TableControl （格式） 的 TableRowEntry EntrySelectedBy 項目</span><span class="sxs-lookup"><span data-stu-id="687d0-134">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="687d0-135">TableControl （格式） 的 TableRowEntry TableColumnItems 項目</span><span class="sxs-lookup"><span data-stu-id="687d0-135">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="687d0-136">TableRowEntries TableControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="687d0-136">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="687d0-137">TableControl （格式） 的 TableRowEntries TableRowEntry 項目</span><span class="sxs-lookup"><span data-stu-id="687d0-137">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[<span data-ttu-id="687d0-138">如 TableRowEntry 包裝項目，如 TableCntrol （格式）</span><span class="sxs-lookup"><span data-stu-id="687d0-138">Wrap Element for TableRowEntry for TableCntrol (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrl-format.md)

[<span data-ttu-id="687d0-139">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="687d0-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
