---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 TableColumnHeader 的標籤元素 (格式)
description: TableControl 之 TableColumnHeader 的標籤元素 (格式)
ms.openlocfilehash: fe4c209903c04e683b44e2bdcbf381adb6874ace
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667788"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="e084a-103">TableControl 之 TableColumnHeader 的標籤元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e084a-103">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="e084a-104">定義顯示在資料行頂端的標籤。</span><span class="sxs-lookup"><span data-stu-id="e084a-104">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="e084a-105">定義資料表視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="e084a-105">This element is used when defining a table view.</span></span>

<span data-ttu-id="e084a-106">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) TableControl 元素 (format) TableHeaders 元素 for TableControl (Format) 之 tablecolumnheader TableHeaders for TableControl for 之 tablecolumnheader (format) TableControl for (格式) </span><span class="sxs-lookup"><span data-stu-id="e084a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e084a-107">語法</span><span class="sxs-lookup"><span data-stu-id="e084a-107">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="e084a-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e084a-108">Attributes and Elements</span></span>

<span data-ttu-id="e084a-109">下列章節說明屬性、子專案和元素的父元素 `Label` 。</span><span class="sxs-lookup"><span data-stu-id="e084a-109">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="e084a-110">每個資料行只允許一個標籤。</span><span class="sxs-lookup"><span data-stu-id="e084a-110">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="e084a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e084a-111">Attributes</span></span>

<span data-ttu-id="e084a-112">無。</span><span class="sxs-lookup"><span data-stu-id="e084a-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e084a-113">子元素</span><span class="sxs-lookup"><span data-stu-id="e084a-113">Child Elements</span></span>

<span data-ttu-id="e084a-114">無。</span><span class="sxs-lookup"><span data-stu-id="e084a-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e084a-115">父項目</span><span class="sxs-lookup"><span data-stu-id="e084a-115">Parent Elements</span></span>

|<span data-ttu-id="e084a-116">元素</span><span class="sxs-lookup"><span data-stu-id="e084a-116">Element</span></span>|<span data-ttu-id="e084a-117">描述</span><span class="sxs-lookup"><span data-stu-id="e084a-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e084a-118">適用于 TableHeaders 的 TableControl (格式的之 tablecolumnheader 元素) </span><span class="sxs-lookup"><span data-stu-id="e084a-118">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="e084a-119">定義資料表之資料行的標籤、寬度和對齊方式。</span><span class="sxs-lookup"><span data-stu-id="e084a-119">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e084a-120">文字值</span><span class="sxs-lookup"><span data-stu-id="e084a-120">Text Value</span></span>

<span data-ttu-id="e084a-121">指定在資料表資料行頂端顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="e084a-121">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="e084a-122">資料行標籤沒有受限的字元。</span><span class="sxs-lookup"><span data-stu-id="e084a-122">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="e084a-123">備註</span><span class="sxs-lookup"><span data-stu-id="e084a-123">Remarks</span></span>

<span data-ttu-id="e084a-124">如果未指定標籤，則會使用其值顯示在資料列中的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="e084a-124">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="e084a-125">如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="e084a-125">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e084a-126">範例</span><span class="sxs-lookup"><span data-stu-id="e084a-126">Example</span></span>

<span data-ttu-id="e084a-127">此範例顯示 `TableColumnHeader` 其標籤為 "Column 1" 的元素。</span><span class="sxs-lookup"><span data-stu-id="e084a-127">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="e084a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e084a-128">See Also</span></span>

[<span data-ttu-id="e084a-129">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="e084a-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e084a-130">TableColumnHeader 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e084a-130">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="e084a-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="e084a-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
