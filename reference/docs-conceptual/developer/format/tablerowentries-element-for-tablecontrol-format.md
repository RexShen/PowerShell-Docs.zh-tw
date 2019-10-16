---
title: TableControl 的 TableRowEntries 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368147"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="33539-102">TableControl 的 TableRowEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="33539-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="33539-103">定義資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="33539-103">Defines the rows of the table.</span></span>

<span data-ttu-id="33539-104">TableControl （格式）的設定元素（格式） ViewDefinitions 元素（格式） TableControl 元素（格式） TableRowEntries 元素</span><span class="sxs-lookup"><span data-stu-id="33539-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="33539-105">語法</span><span class="sxs-lookup"><span data-stu-id="33539-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="33539-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="33539-106">Attributes and Elements</span></span>

<span data-ttu-id="33539-107">下列各節說明 `TableRowEntries` 元素的屬性、子專案和父元素。</span><span class="sxs-lookup"><span data-stu-id="33539-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="33539-108">屬性</span><span class="sxs-lookup"><span data-stu-id="33539-108">Attributes</span></span>

<span data-ttu-id="33539-109">無。</span><span class="sxs-lookup"><span data-stu-id="33539-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="33539-110">子元素</span><span class="sxs-lookup"><span data-stu-id="33539-110">Child Elements</span></span>

|<span data-ttu-id="33539-111">元素</span><span class="sxs-lookup"><span data-stu-id="33539-111">Element</span></span>|<span data-ttu-id="33539-112">描述</span><span class="sxs-lookup"><span data-stu-id="33539-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33539-113">TableControl 之 TableRowEntries 的 TableRowEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="33539-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="33539-114">必要元素。</span><span class="sxs-lookup"><span data-stu-id="33539-114">Required element.</span></span><br /><br /> <span data-ttu-id="33539-115">定義在資料表的資料列中顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="33539-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="33539-116">父元素</span><span class="sxs-lookup"><span data-stu-id="33539-116">Parent Elements</span></span>

|<span data-ttu-id="33539-117">元素</span><span class="sxs-lookup"><span data-stu-id="33539-117">Element</span></span>|<span data-ttu-id="33539-118">描述</span><span class="sxs-lookup"><span data-stu-id="33539-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33539-119">TableControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="33539-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="33539-120">定義視圖的資料表格式。</span><span class="sxs-lookup"><span data-stu-id="33539-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="33539-121">備註</span><span class="sxs-lookup"><span data-stu-id="33539-121">Remarks</span></span>

<span data-ttu-id="33539-122">您必須為數據表視圖指定一個或多個 @no__t 0 元素。</span><span class="sxs-lookup"><span data-stu-id="33539-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="33539-123">可以新增的 @no__t 0 元素數目沒有最大限制，也不會有其順序重要性。</span><span class="sxs-lookup"><span data-stu-id="33539-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="33539-124">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="33539-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="33539-125">範例</span><span class="sxs-lookup"><span data-stu-id="33539-125">Example</span></span>

<span data-ttu-id="33539-126">下列範例顯示的 `TableRowEntries` 元素會定義一個資料列，其中會顯示[system.web](/dotnet/api/System.Diagnostics.Process)物件的兩個屬性值。</span><span class="sxs-lookup"><span data-stu-id="33539-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="33539-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33539-127">See Also</span></span>

[<span data-ttu-id="33539-128">建立資料表視圖</span><span class="sxs-lookup"><span data-stu-id="33539-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="33539-129">TableControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="33539-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="33539-130">TableRowEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="33539-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="33539-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="33539-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
