---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 TableColumnHeader 的寬度元素 (格式)
description: TableControl 之 TableColumnHeader 的寬度元素 (格式)
ms.openlocfilehash: bde84f1d33b3d6b3b8c4462f870f978611cb434b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658258"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="79b65-103">TableControl 之 TableColumnHeader 的寬度元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="79b65-103">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="79b65-104">定義資料行) 字元 (的寬度。</span><span class="sxs-lookup"><span data-stu-id="79b65-104">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="79b65-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) TableControl 元素 (format) TableHeaders 元素 for TableControl (Format) 之 tablecolumnheader Element TableHeaders for TableControl (format) 之 tablecolumnheader for TableControl 的 (Width 元素) 格式</span><span class="sxs-lookup"><span data-stu-id="79b65-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="79b65-106">語法</span><span class="sxs-lookup"><span data-stu-id="79b65-106">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="79b65-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="79b65-107">Attributes and Elements</span></span>

<span data-ttu-id="79b65-108">下列各節描述定義資料行標頭時所使用專案的屬性、子項目和父元素 `Width` 。</span><span class="sxs-lookup"><span data-stu-id="79b65-108">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="79b65-109">屬性</span><span class="sxs-lookup"><span data-stu-id="79b65-109">Attributes</span></span>

<span data-ttu-id="79b65-110">無。</span><span class="sxs-lookup"><span data-stu-id="79b65-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="79b65-111">子元素</span><span class="sxs-lookup"><span data-stu-id="79b65-111">Child Elements</span></span>

<span data-ttu-id="79b65-112">無。</span><span class="sxs-lookup"><span data-stu-id="79b65-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="79b65-113">父項目</span><span class="sxs-lookup"><span data-stu-id="79b65-113">Parent Elements</span></span>

|<span data-ttu-id="79b65-114">元素</span><span class="sxs-lookup"><span data-stu-id="79b65-114">Element</span></span>|<span data-ttu-id="79b65-115">描述</span><span class="sxs-lookup"><span data-stu-id="79b65-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="79b65-116">適用于 TableHeaders 的 TableControl (格式的之 tablecolumnheader 元素) </span><span class="sxs-lookup"><span data-stu-id="79b65-116">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="79b65-117">定義資料表之資料行的標籤、寬度和對齊方式。</span><span class="sxs-lookup"><span data-stu-id="79b65-117">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="79b65-118">文字值</span><span class="sxs-lookup"><span data-stu-id="79b65-118">Text Value</span></span>

<span data-ttu-id="79b65-119">如果有可能的話，請將寬度 (指定為大於所顯示內容值長度的字元) 。</span><span class="sxs-lookup"><span data-stu-id="79b65-119">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="79b65-120">備註</span><span class="sxs-lookup"><span data-stu-id="79b65-120">Remarks</span></span>

<span data-ttu-id="79b65-121">如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="79b65-121">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="79b65-122">範例</span><span class="sxs-lookup"><span data-stu-id="79b65-122">Example</span></span>

<span data-ttu-id="79b65-123">下列範例 `TableColumnHeader` 會顯示其寬度為16個字元的元素。</span><span class="sxs-lookup"><span data-stu-id="79b65-123">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="79b65-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79b65-124">See Also</span></span>

[<span data-ttu-id="79b65-125">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="79b65-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="79b65-126">適用于 TableHeader 的 TableControl (格式的之 tablecolumnheader 元素) </span><span class="sxs-lookup"><span data-stu-id="79b65-126">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="79b65-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="79b65-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
