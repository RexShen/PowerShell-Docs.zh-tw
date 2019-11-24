---
title: TableControl 之之 tablecolumnheader 的對齊元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364377"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="55655-102">TableControl 之 TableColumnHeader 的對齊元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="55655-102">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="55655-103">定義資料行標頭中的資料顯示方式。</span><span class="sxs-lookup"><span data-stu-id="55655-103">Defines how the data in a column header is displayed.</span></span>

<span data-ttu-id="55655-104">之 tablecolumnheader 的設定元素（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（格式） TableHeaders 元素（格式）之 tablecolumnheader 元素（格式）對齊元素</span><span class="sxs-lookup"><span data-stu-id="55655-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element (Format) TableColumnHeader Element (Format) Alignment Element for TableColumnHeader (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="55655-105">語法</span><span class="sxs-lookup"><span data-stu-id="55655-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="55655-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="55655-106">Attributes and Elements</span></span>

<span data-ttu-id="55655-107">下列各節描述 `Alignment` 專案的屬性、子專案和父項目。</span><span class="sxs-lookup"><span data-stu-id="55655-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="55655-108">屬性</span><span class="sxs-lookup"><span data-stu-id="55655-108">Attributes</span></span>

<span data-ttu-id="55655-109">無。</span><span class="sxs-lookup"><span data-stu-id="55655-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="55655-110">子元素</span><span class="sxs-lookup"><span data-stu-id="55655-110">Child Elements</span></span>

<span data-ttu-id="55655-111">無。</span><span class="sxs-lookup"><span data-stu-id="55655-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="55655-112">父元素</span><span class="sxs-lookup"><span data-stu-id="55655-112">Parent Elements</span></span>

|<span data-ttu-id="55655-113">項目</span><span class="sxs-lookup"><span data-stu-id="55655-113">Element</span></span>|<span data-ttu-id="55655-114">說明</span><span class="sxs-lookup"><span data-stu-id="55655-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="55655-115">之 tablecolumnheader 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="55655-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="55655-116">定義資料表資料行的標籤、寬度和對齊方式。</span><span class="sxs-lookup"><span data-stu-id="55655-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="55655-117">文字值</span><span class="sxs-lookup"><span data-stu-id="55655-117">Text Value</span></span>

<span data-ttu-id="55655-118">指定下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="55655-118">Specify one of the following values.</span></span> <span data-ttu-id="55655-119">這些值不會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="55655-119">These values are not case-sensitive.</span></span>

<span data-ttu-id="55655-120">靠左對齊資料行中顯示的資料。如果未指定此元素，則為預設值。</span><span class="sxs-lookup"><span data-stu-id="55655-120">Left Aligns the data displayed in the column on the left This is the default if this element is not specified.</span></span>

<span data-ttu-id="55655-121">靠右對齊右側資料行中顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="55655-121">Right Aligns the data displayed in the column on the right.</span></span>

<span data-ttu-id="55655-122">置中：在資料行中顯示的資料中心。</span><span class="sxs-lookup"><span data-stu-id="55655-122">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="55655-123">備註</span><span class="sxs-lookup"><span data-stu-id="55655-123">Remarks</span></span>

<span data-ttu-id="55655-124">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="55655-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="55655-125">範例</span><span class="sxs-lookup"><span data-stu-id="55655-125">Example</span></span>

<span data-ttu-id="55655-126">這個範例會顯示其資料在左側對齊的 `TableColumnHeader` 元素。</span><span class="sxs-lookup"><span data-stu-id="55655-126">This example shows a `TableColumnHeader` element whose data is aligned on the left.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="55655-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55655-127">See Also</span></span>

[<span data-ttu-id="55655-128">建立資料表視圖</span><span class="sxs-lookup"><span data-stu-id="55655-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="55655-129">之 tablecolumnheader 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="55655-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="55655-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="55655-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
