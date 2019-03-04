---
title: TableRowEntries TableControl （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: d93750f919c1075f173dc9ac70324cc003e36879
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862184"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="9d388-102">TableControl 的 TableRowEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9d388-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="9d388-103">定義資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="9d388-103">Defines the rows of the table.</span></span>

<span data-ttu-id="9d388-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 TableControl （格式）</span><span class="sxs-lookup"><span data-stu-id="9d388-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9d388-105">語法</span><span class="sxs-lookup"><span data-stu-id="9d388-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9d388-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="9d388-106">Attributes and Elements</span></span>

<span data-ttu-id="9d388-107">下列各節說明屬性、 子項目和父項目`TableRowEntries`項目。</span><span class="sxs-lookup"><span data-stu-id="9d388-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9d388-108">屬性</span><span class="sxs-lookup"><span data-stu-id="9d388-108">Attributes</span></span>

<span data-ttu-id="9d388-109">無。</span><span class="sxs-lookup"><span data-stu-id="9d388-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9d388-110">子元素</span><span class="sxs-lookup"><span data-stu-id="9d388-110">Child Elements</span></span>

|<span data-ttu-id="9d388-111">元素</span><span class="sxs-lookup"><span data-stu-id="9d388-111">Element</span></span>|<span data-ttu-id="9d388-112">描述</span><span class="sxs-lookup"><span data-stu-id="9d388-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9d388-113">TableControl （格式） 的 TableRowEntries TableRowEntry 項目</span><span class="sxs-lookup"><span data-stu-id="9d388-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|<span data-ttu-id="9d388-114">必要項目。</span><span class="sxs-lookup"><span data-stu-id="9d388-114">Required element.</span></span><br /><br /> <span data-ttu-id="9d388-115">定義會顯示在資料表資料列的資料。</span><span class="sxs-lookup"><span data-stu-id="9d388-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9d388-116">父元素</span><span class="sxs-lookup"><span data-stu-id="9d388-116">Parent Elements</span></span>

|<span data-ttu-id="9d388-117">元素</span><span class="sxs-lookup"><span data-stu-id="9d388-117">Element</span></span>|<span data-ttu-id="9d388-118">描述</span><span class="sxs-lookup"><span data-stu-id="9d388-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9d388-119">TableControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="9d388-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="9d388-120">定義檢視的資料表格式。</span><span class="sxs-lookup"><span data-stu-id="9d388-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9d388-121">備註</span><span class="sxs-lookup"><span data-stu-id="9d388-121">Remarks</span></span>

<span data-ttu-id="9d388-122">您必須指定一或多個`TableRowEntry`資料表檢視項目。</span><span class="sxs-lookup"><span data-stu-id="9d388-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="9d388-123">沒有任何數目的最大限制`TableRowEntry`可以加入的項目也不是重要的順序。</span><span class="sxs-lookup"><span data-stu-id="9d388-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="9d388-124">資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="9d388-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="9d388-125">範例</span><span class="sxs-lookup"><span data-stu-id="9d388-125">Example</span></span>

<span data-ttu-id="9d388-126">下列範例所示`TableRowEntries`項目，定義會顯示兩個屬性的值的資料列[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件。</span><span class="sxs-lookup"><span data-stu-id="9d388-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9d388-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d388-127">See Also</span></span>

[<span data-ttu-id="9d388-128">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="9d388-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="9d388-129">TableControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="9d388-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="9d388-130">TableRowEntry 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="9d388-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[<span data-ttu-id="9d388-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="9d388-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
