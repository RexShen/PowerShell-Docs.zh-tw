---
title: TableControl （格式） 的 TableRowEntry TableColumnItems 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075387"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="72830-102">TableControl 之 TableRowEntry 的 TableColumnItems 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="72830-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="72830-103">定義屬性或其值會顯示資料列中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="72830-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="72830-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 TableControl （格式） TableRowEntry TableRowEntries TableControl （格式） 的項目TableControl （格式） 的 TableControlEntry TableColumnItems 項目</span><span class="sxs-lookup"><span data-stu-id="72830-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="72830-105">語法</span><span class="sxs-lookup"><span data-stu-id="72830-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="72830-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="72830-106">Attributes and Elements</span></span>

<span data-ttu-id="72830-107">下列各節說明屬性、 子項目和父項目`TableColumnItems`項目。</span><span class="sxs-lookup"><span data-stu-id="72830-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="72830-108">屬性</span><span class="sxs-lookup"><span data-stu-id="72830-108">Attributes</span></span>

<span data-ttu-id="72830-109">無。</span><span class="sxs-lookup"><span data-stu-id="72830-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="72830-110">子元素</span><span class="sxs-lookup"><span data-stu-id="72830-110">Child Elements</span></span>

|<span data-ttu-id="72830-111">元素</span><span class="sxs-lookup"><span data-stu-id="72830-111">Element</span></span>|<span data-ttu-id="72830-112">描述</span><span class="sxs-lookup"><span data-stu-id="72830-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="72830-113">TableControl （格式） 的 TableColumnItems TableColumnItem 項目</span><span class="sxs-lookup"><span data-stu-id="72830-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="72830-114">必要項目。</span><span class="sxs-lookup"><span data-stu-id="72830-114">Required element.</span></span><br /><br /> <span data-ttu-id="72830-115">定義屬性或其值會顯示資料列的資料行中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="72830-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="72830-116">父項目</span><span class="sxs-lookup"><span data-stu-id="72830-116">Parent Elements</span></span>

|<span data-ttu-id="72830-117">項目</span><span class="sxs-lookup"><span data-stu-id="72830-117">Element</span></span>|<span data-ttu-id="72830-118">描述</span><span class="sxs-lookup"><span data-stu-id="72830-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="72830-119">TableControl （格式） 的 TableRowEntries TableRowEntry 項目</span><span class="sxs-lookup"><span data-stu-id="72830-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="72830-120">定義會顯示在資料表資料列的資料。</span><span class="sxs-lookup"><span data-stu-id="72830-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="72830-121">備註</span><span class="sxs-lookup"><span data-stu-id="72830-121">Remarks</span></span>

<span data-ttu-id="72830-122">A `TableColumnItem` ，則需要每個資料行的資料列元素。</span><span class="sxs-lookup"><span data-stu-id="72830-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="72830-123">第一個項目會顯示在第一個資料行，第二個項目，在第二個資料行，依此類推。</span><span class="sxs-lookup"><span data-stu-id="72830-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="72830-124">資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="72830-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="72830-125">範例</span><span class="sxs-lookup"><span data-stu-id="72830-125">Example</span></span>

<span data-ttu-id="72830-126">下列範例所示`TableColumnItems`定義的三個屬性的項目[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件。</span><span class="sxs-lookup"><span data-stu-id="72830-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="72830-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72830-127">See Also</span></span>

[<span data-ttu-id="72830-128">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="72830-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="72830-129">TableColumnItem 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="72830-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="72830-130">TableRowEntry 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="72830-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="72830-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="72830-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
