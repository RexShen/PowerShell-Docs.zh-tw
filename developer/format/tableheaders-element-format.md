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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856874"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="313af-102">TableHeaders 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="313af-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="313af-103">定義資料表的資料行的標頭。</span><span class="sxs-lookup"><span data-stu-id="313af-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="313af-104">ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableHeaders 元素 TableControl （格式）</span><span class="sxs-lookup"><span data-stu-id="313af-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="313af-105">語法</span><span class="sxs-lookup"><span data-stu-id="313af-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="313af-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="313af-106">Attributes and Elements</span></span>

<span data-ttu-id="313af-107">下列各節說明屬性、 子項目和父項目`TableHeaders`項目。</span><span class="sxs-lookup"><span data-stu-id="313af-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="313af-108">必須為每個屬性之物件的顯示，則為子項目。</span><span class="sxs-lookup"><span data-stu-id="313af-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="313af-109">資料行標頭資訊會顯示子項目所指定的順序。</span><span class="sxs-lookup"><span data-stu-id="313af-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="313af-110">屬性</span><span class="sxs-lookup"><span data-stu-id="313af-110">Attributes</span></span>

<span data-ttu-id="313af-111">無。</span><span class="sxs-lookup"><span data-stu-id="313af-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="313af-112">子元素</span><span class="sxs-lookup"><span data-stu-id="313af-112">Child Elements</span></span>

|<span data-ttu-id="313af-113">元素</span><span class="sxs-lookup"><span data-stu-id="313af-113">Element</span></span>|<span data-ttu-id="313af-114">描述</span><span class="sxs-lookup"><span data-stu-id="313af-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="313af-115">TableColumnHeader 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="313af-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="313af-116">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="313af-116">Optional element.</span></span><br /><br /> <span data-ttu-id="313af-117">定義標籤、 寬度和資料行的資料表檢視資料的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="313af-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="313af-118">父元素</span><span class="sxs-lookup"><span data-stu-id="313af-118">Parent Elements</span></span>

|<span data-ttu-id="313af-119">元素</span><span class="sxs-lookup"><span data-stu-id="313af-119">Element</span></span>|<span data-ttu-id="313af-120">描述</span><span class="sxs-lookup"><span data-stu-id="313af-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="313af-121">TableControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="313af-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="313af-122">定義檢視的資料表格式。</span><span class="sxs-lookup"><span data-stu-id="313af-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="313af-123">備註</span><span class="sxs-lookup"><span data-stu-id="313af-123">Remarks</span></span>

<span data-ttu-id="313af-124">資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="313af-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="313af-125">範例</span><span class="sxs-lookup"><span data-stu-id="313af-125">Example</span></span>

<span data-ttu-id="313af-126">此範例示範`TableHeaders`定義兩個資料行的標頭項目。</span><span class="sxs-lookup"><span data-stu-id="313af-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="313af-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="313af-127">See Also</span></span>

[<span data-ttu-id="313af-128">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="313af-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="313af-129">TableColumnHeader 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="313af-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="313af-130">TableControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="313af-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="313af-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="313af-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
