---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 TableColumnHeader 的對齊元素 (格式)
description: TableControl 之 TableColumnHeader 的對齊元素 (格式)
ms.openlocfilehash: cf8b90c12c28951283b5870186e2c88d427318a5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666819"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="2cef2-103">TableControl 之 TableColumnHeader 的對齊元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2cef2-103">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="2cef2-104">定義如何顯示資料行標題中的資料。</span><span class="sxs-lookup"><span data-stu-id="2cef2-104">Defines how the data in a column header is displayed.</span></span>

<span data-ttu-id="2cef2-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) TableControl 元素 (format) TableHeaders 元素 (format) 之 tablecolumnheader 專案 (格式)  (的對齊元素) 格式</span><span class="sxs-lookup"><span data-stu-id="2cef2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element (Format) TableColumnHeader Element (Format) Alignment Element for TableColumnHeader (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2cef2-106">語法</span><span class="sxs-lookup"><span data-stu-id="2cef2-106">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2cef2-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2cef2-107">Attributes and Elements</span></span>

<span data-ttu-id="2cef2-108">下列各節描述專案的屬性、子項目和父元素 `Alignment` 。</span><span class="sxs-lookup"><span data-stu-id="2cef2-108">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2cef2-109">屬性</span><span class="sxs-lookup"><span data-stu-id="2cef2-109">Attributes</span></span>

<span data-ttu-id="2cef2-110">無。</span><span class="sxs-lookup"><span data-stu-id="2cef2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2cef2-111">子元素</span><span class="sxs-lookup"><span data-stu-id="2cef2-111">Child Elements</span></span>

<span data-ttu-id="2cef2-112">無。</span><span class="sxs-lookup"><span data-stu-id="2cef2-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2cef2-113">父項目</span><span class="sxs-lookup"><span data-stu-id="2cef2-113">Parent Elements</span></span>

|<span data-ttu-id="2cef2-114">元素</span><span class="sxs-lookup"><span data-stu-id="2cef2-114">Element</span></span>|<span data-ttu-id="2cef2-115">描述</span><span class="sxs-lookup"><span data-stu-id="2cef2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2cef2-116">TableColumnHeader 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2cef2-116">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="2cef2-117">定義資料表之資料行的標籤、寬度和對齊方式。</span><span class="sxs-lookup"><span data-stu-id="2cef2-117">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2cef2-118">文字值</span><span class="sxs-lookup"><span data-stu-id="2cef2-118">Text Value</span></span>

<span data-ttu-id="2cef2-119">指定下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="2cef2-119">Specify one of the following values.</span></span> <span data-ttu-id="2cef2-120">這些值不會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="2cef2-120">These values are not case-sensitive.</span></span>

<span data-ttu-id="2cef2-121">如果未指定這個元素，則靠左對齊資料行中顯示的資料，這是預設值。</span><span class="sxs-lookup"><span data-stu-id="2cef2-121">Left Aligns the data displayed in the column on the left This is the default if this element is not specified.</span></span>

<span data-ttu-id="2cef2-122">靠右對齊資料行中顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="2cef2-122">Right Aligns the data displayed in the column on the right.</span></span>

<span data-ttu-id="2cef2-123">置中：將資料行中顯示的資料置中。</span><span class="sxs-lookup"><span data-stu-id="2cef2-123">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="2cef2-124">備註</span><span class="sxs-lookup"><span data-stu-id="2cef2-124">Remarks</span></span>

<span data-ttu-id="2cef2-125">如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="2cef2-125">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2cef2-126">範例</span><span class="sxs-lookup"><span data-stu-id="2cef2-126">Example</span></span>

<span data-ttu-id="2cef2-127">這個範例會顯示 `TableColumnHeader` 其資料在左邊對齊的元素。</span><span class="sxs-lookup"><span data-stu-id="2cef2-127">This example shows a `TableColumnHeader` element whose data is aligned on the left.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="2cef2-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cef2-128">See Also</span></span>

[<span data-ttu-id="2cef2-129">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="2cef2-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2cef2-130">TableColumnHeader 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2cef2-130">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="2cef2-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="2cef2-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
