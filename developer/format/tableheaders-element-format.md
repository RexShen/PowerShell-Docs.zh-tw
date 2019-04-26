---
title: TableHeaders 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075404"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="12052-102">TableHeaders 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="12052-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="12052-103">定義資料表的資料行的標頭。</span><span class="sxs-lookup"><span data-stu-id="12052-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="12052-104">ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableHeaders 元素 TableControl （格式）</span><span class="sxs-lookup"><span data-stu-id="12052-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="12052-105">語法</span><span class="sxs-lookup"><span data-stu-id="12052-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="12052-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="12052-106">Attributes and Elements</span></span>

<span data-ttu-id="12052-107">下列各節說明屬性、 子項目和父項目`TableHeaders`項目。</span><span class="sxs-lookup"><span data-stu-id="12052-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="12052-108">必須為每個屬性之物件的顯示，則為子項目。</span><span class="sxs-lookup"><span data-stu-id="12052-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="12052-109">資料行標頭資訊會顯示子項目所指定的順序。</span><span class="sxs-lookup"><span data-stu-id="12052-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="12052-110">屬性</span><span class="sxs-lookup"><span data-stu-id="12052-110">Attributes</span></span>

<span data-ttu-id="12052-111">無。</span><span class="sxs-lookup"><span data-stu-id="12052-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="12052-112">子元素</span><span class="sxs-lookup"><span data-stu-id="12052-112">Child Elements</span></span>

|<span data-ttu-id="12052-113">元素</span><span class="sxs-lookup"><span data-stu-id="12052-113">Element</span></span>|<span data-ttu-id="12052-114">描述</span><span class="sxs-lookup"><span data-stu-id="12052-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="12052-115">TableColumnHeader 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="12052-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="12052-116">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="12052-116">Optional element.</span></span><br /><br /> <span data-ttu-id="12052-117">定義標籤、 寬度和資料行的資料表檢視資料的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="12052-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="12052-118">父項目</span><span class="sxs-lookup"><span data-stu-id="12052-118">Parent Elements</span></span>

|<span data-ttu-id="12052-119">項目</span><span class="sxs-lookup"><span data-stu-id="12052-119">Element</span></span>|<span data-ttu-id="12052-120">描述</span><span class="sxs-lookup"><span data-stu-id="12052-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="12052-121">TableControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="12052-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="12052-122">定義檢視的資料表格式。</span><span class="sxs-lookup"><span data-stu-id="12052-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="12052-123">備註</span><span class="sxs-lookup"><span data-stu-id="12052-123">Remarks</span></span>

<span data-ttu-id="12052-124">資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="12052-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="12052-125">範例</span><span class="sxs-lookup"><span data-stu-id="12052-125">Example</span></span>

<span data-ttu-id="12052-126">此範例示範`TableHeaders`定義兩個資料行的標頭項目。</span><span class="sxs-lookup"><span data-stu-id="12052-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
  <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a><span data-ttu-id="12052-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12052-127">See Also</span></span>

[<span data-ttu-id="12052-128">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="12052-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="12052-129">TableColumnHeader 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="12052-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="12052-130">TableControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="12052-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="12052-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="12052-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
