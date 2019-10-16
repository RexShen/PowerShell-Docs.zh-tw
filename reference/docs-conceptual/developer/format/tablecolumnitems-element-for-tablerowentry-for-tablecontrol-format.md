---
title: TableControl 之 TableRowEntry 的 TableColumnItems 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361807"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="4f462-102">TableControl 之 TableRowEntry 的 TableColumnItems 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4f462-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="4f462-103">定義屬性或腳本，其值會顯示在資料列中。</span><span class="sxs-lookup"><span data-stu-id="4f462-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="4f462-104">TableRowEntry for TableRowEntries 之 TableControl （Format） TableControl 元素的 Configuration 元素（格式） ViewDefinitions 元素（格式） TableRowEntries 元素（格式）TableControl 之 TableControlEntry 的 TableColumnItems 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4f462-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4f462-105">語法</span><span class="sxs-lookup"><span data-stu-id="4f462-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4f462-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="4f462-106">Attributes and Elements</span></span>

<span data-ttu-id="4f462-107">下列各節說明 `TableColumnItems` 元素的屬性、子專案和父元素。</span><span class="sxs-lookup"><span data-stu-id="4f462-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4f462-108">屬性</span><span class="sxs-lookup"><span data-stu-id="4f462-108">Attributes</span></span>

<span data-ttu-id="4f462-109">無。</span><span class="sxs-lookup"><span data-stu-id="4f462-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4f462-110">子元素</span><span class="sxs-lookup"><span data-stu-id="4f462-110">Child Elements</span></span>

|<span data-ttu-id="4f462-111">元素</span><span class="sxs-lookup"><span data-stu-id="4f462-111">Element</span></span>|<span data-ttu-id="4f462-112">描述</span><span class="sxs-lookup"><span data-stu-id="4f462-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4f462-113">TableControl 之 TableColumnItems 的之 tablecolumnitem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4f462-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="4f462-114">必要元素。</span><span class="sxs-lookup"><span data-stu-id="4f462-114">Required element.</span></span><br /><br /> <span data-ttu-id="4f462-115">定義屬性或腳本，其值會顯示在資料列的資料行中。</span><span class="sxs-lookup"><span data-stu-id="4f462-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4f462-116">父元素</span><span class="sxs-lookup"><span data-stu-id="4f462-116">Parent Elements</span></span>

|<span data-ttu-id="4f462-117">元素</span><span class="sxs-lookup"><span data-stu-id="4f462-117">Element</span></span>|<span data-ttu-id="4f462-118">描述</span><span class="sxs-lookup"><span data-stu-id="4f462-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4f462-119">TableControl 之 TableRowEntries 的 TableRowEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4f462-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="4f462-120">定義在資料表的資料列中顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="4f462-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4f462-121">備註</span><span class="sxs-lookup"><span data-stu-id="4f462-121">Remarks</span></span>

<span data-ttu-id="4f462-122">資料列的每個資料行都需要 `TableColumnItem` 元素。</span><span class="sxs-lookup"><span data-stu-id="4f462-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="4f462-123">第一個專案會顯示在第一個資料行、第二個數據行中的第二個專案，依此類推。</span><span class="sxs-lookup"><span data-stu-id="4f462-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="4f462-124">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="4f462-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4f462-125">範例</span><span class="sxs-lookup"><span data-stu-id="4f462-125">Example</span></span>

<span data-ttu-id="4f462-126">下列範例顯示的 `TableColumnItems` 元素會定義[system.servicemodel 物件的](/dotnet/api/System.Diagnostics.Process)三個屬性。</span><span class="sxs-lookup"><span data-stu-id="4f462-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4f462-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f462-127">See Also</span></span>

[<span data-ttu-id="4f462-128">建立資料表視圖</span><span class="sxs-lookup"><span data-stu-id="4f462-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="4f462-129">之 tablecolumnitem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4f462-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="4f462-130">TableRowEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4f462-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="4f462-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="4f462-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
