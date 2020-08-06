---
title: TableControl (格式的之 tablecolumnheader 的對齊元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1bf395b84af90d725c14b2f0ef569f72b5fcc613
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783920"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="a80d2-102">TableControl 之 TableColumnHeader 的對齊元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a80d2-102">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="a80d2-103">定義資料行標頭中的資料顯示方式。</span><span class="sxs-lookup"><span data-stu-id="a80d2-103">Defines how the data in a column header is displayed.</span></span>

<span data-ttu-id="a80d2-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 專案 (格式) TableHeaders 專案 (格式) 之 tablecolumnheader 專案 (格式) 之 tablecolumnheader (格式的對齊元素) </span><span class="sxs-lookup"><span data-stu-id="a80d2-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element (Format) TableColumnHeader Element (Format) Alignment Element for TableColumnHeader (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a80d2-105">語法</span><span class="sxs-lookup"><span data-stu-id="a80d2-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a80d2-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a80d2-106">Attributes and Elements</span></span>

<span data-ttu-id="a80d2-107">下列各節描述元素的屬性、子專案和父項目 `Alignment` 。</span><span class="sxs-lookup"><span data-stu-id="a80d2-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a80d2-108">屬性</span><span class="sxs-lookup"><span data-stu-id="a80d2-108">Attributes</span></span>

<span data-ttu-id="a80d2-109">無。</span><span class="sxs-lookup"><span data-stu-id="a80d2-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a80d2-110">子元素</span><span class="sxs-lookup"><span data-stu-id="a80d2-110">Child Elements</span></span>

<span data-ttu-id="a80d2-111">無。</span><span class="sxs-lookup"><span data-stu-id="a80d2-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a80d2-112">父項目</span><span class="sxs-lookup"><span data-stu-id="a80d2-112">Parent Elements</span></span>

|<span data-ttu-id="a80d2-113">元素</span><span class="sxs-lookup"><span data-stu-id="a80d2-113">Element</span></span>|<span data-ttu-id="a80d2-114">描述</span><span class="sxs-lookup"><span data-stu-id="a80d2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a80d2-115">TableColumnHeader 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a80d2-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="a80d2-116">定義資料表資料行的標籤、寬度和對齊方式。</span><span class="sxs-lookup"><span data-stu-id="a80d2-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a80d2-117">文字值</span><span class="sxs-lookup"><span data-stu-id="a80d2-117">Text Value</span></span>

<span data-ttu-id="a80d2-118">指定下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="a80d2-118">Specify one of the following values.</span></span> <span data-ttu-id="a80d2-119">這些值不會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="a80d2-119">These values are not case-sensitive.</span></span>

<span data-ttu-id="a80d2-120">靠左對齊資料行中顯示的資料。如果未指定此元素，則為預設值。</span><span class="sxs-lookup"><span data-stu-id="a80d2-120">Left Aligns the data displayed in the column on the left This is the default if this element is not specified.</span></span>

<span data-ttu-id="a80d2-121">靠右對齊右側資料行中顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="a80d2-121">Right Aligns the data displayed in the column on the right.</span></span>

<span data-ttu-id="a80d2-122">置中：在資料行中顯示的資料中心。</span><span class="sxs-lookup"><span data-stu-id="a80d2-122">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="a80d2-123">備註</span><span class="sxs-lookup"><span data-stu-id="a80d2-123">Remarks</span></span>

<span data-ttu-id="a80d2-124">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="a80d2-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a80d2-125">範例</span><span class="sxs-lookup"><span data-stu-id="a80d2-125">Example</span></span>

<span data-ttu-id="a80d2-126">這個範例會顯示 `TableColumnHeader` 其資料在左側對齊的元素。</span><span class="sxs-lookup"><span data-stu-id="a80d2-126">This example shows a `TableColumnHeader` element whose data is aligned on the left.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="a80d2-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a80d2-127">See Also</span></span>

[<span data-ttu-id="a80d2-128">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="a80d2-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a80d2-129">TableColumnHeader 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a80d2-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="a80d2-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="a80d2-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
