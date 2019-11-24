---
title: TableHeaders 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361817"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="e5df9-102">TableHeaders 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e5df9-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="e5df9-103">定義資料表之資料行的標頭。</span><span class="sxs-lookup"><span data-stu-id="e5df9-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="e5df9-104">TableControl 的 ViewDefinitions 元素（格式） View 元素（Format） TableControl 元素（格式） TableHeaders 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e5df9-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5df9-105">語法</span><span class="sxs-lookup"><span data-stu-id="e5df9-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5df9-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="e5df9-106">Attributes and Elements</span></span>

<span data-ttu-id="e5df9-107">下列各節描述 `TableHeaders` 專案的屬性、子專案和父項目。</span><span class="sxs-lookup"><span data-stu-id="e5df9-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="e5df9-108">要顯示之物件的每個屬性都必須要有一個子項目。</span><span class="sxs-lookup"><span data-stu-id="e5df9-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="e5df9-109">資料行標頭資訊會以指定子項目的順序顯示。</span><span class="sxs-lookup"><span data-stu-id="e5df9-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5df9-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e5df9-110">Attributes</span></span>

<span data-ttu-id="e5df9-111">無。</span><span class="sxs-lookup"><span data-stu-id="e5df9-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5df9-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e5df9-112">Child Elements</span></span>

|<span data-ttu-id="e5df9-113">項目</span><span class="sxs-lookup"><span data-stu-id="e5df9-113">Element</span></span>|<span data-ttu-id="e5df9-114">說明</span><span class="sxs-lookup"><span data-stu-id="e5df9-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5df9-115">之 tablecolumnheader 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e5df9-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="e5df9-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e5df9-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e5df9-117">定義資料表視圖之資料行的標籤、寬度和對齊方式。</span><span class="sxs-lookup"><span data-stu-id="e5df9-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e5df9-118">父元素</span><span class="sxs-lookup"><span data-stu-id="e5df9-118">Parent Elements</span></span>

|<span data-ttu-id="e5df9-119">項目</span><span class="sxs-lookup"><span data-stu-id="e5df9-119">Element</span></span>|<span data-ttu-id="e5df9-120">說明</span><span class="sxs-lookup"><span data-stu-id="e5df9-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5df9-121">TableControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e5df9-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="e5df9-122">定義視圖的資料表格式。</span><span class="sxs-lookup"><span data-stu-id="e5df9-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e5df9-123">備註</span><span class="sxs-lookup"><span data-stu-id="e5df9-123">Remarks</span></span>

<span data-ttu-id="e5df9-124">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="e5df9-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e5df9-125">範例</span><span class="sxs-lookup"><span data-stu-id="e5df9-125">Example</span></span>

<span data-ttu-id="e5df9-126">這個範例會顯示定義兩個數據行標頭的 `TableHeaders` 元素。</span><span class="sxs-lookup"><span data-stu-id="e5df9-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e5df9-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5df9-127">See Also</span></span>

[<span data-ttu-id="e5df9-128">建立資料表視圖</span><span class="sxs-lookup"><span data-stu-id="e5df9-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e5df9-129">之 tablecolumnheader 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e5df9-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="e5df9-130">TableControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e5df9-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="e5df9-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="e5df9-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
