---
title: TableControl 之之 tablecolumnheader 的標籤元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365167"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="bc103-102">TableControl 之 TableColumnHeader 的標籤元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bc103-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="bc103-103">定義顯示在資料行頂端的標籤。</span><span class="sxs-lookup"><span data-stu-id="bc103-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="bc103-104">定義資料表視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="bc103-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="bc103-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（format） TableHeaders 元素（適用于之 tablecolumnheader for TableHeaders （Format） Label 元素的 TableControl （format） TableControl 元素）TableControl 的之 tablecolumnheader （格式）</span><span class="sxs-lookup"><span data-stu-id="bc103-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bc103-106">語法</span><span class="sxs-lookup"><span data-stu-id="bc103-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="bc103-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="bc103-107">Attributes and Elements</span></span>

<span data-ttu-id="bc103-108">下列各節說明屬性、子專案，以及 `Label` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="bc103-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="bc103-109">每個資料行只允許一個標籤。</span><span class="sxs-lookup"><span data-stu-id="bc103-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="bc103-110">屬性</span><span class="sxs-lookup"><span data-stu-id="bc103-110">Attributes</span></span>

<span data-ttu-id="bc103-111">無。</span><span class="sxs-lookup"><span data-stu-id="bc103-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bc103-112">子元素</span><span class="sxs-lookup"><span data-stu-id="bc103-112">Child Elements</span></span>

<span data-ttu-id="bc103-113">無。</span><span class="sxs-lookup"><span data-stu-id="bc103-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bc103-114">父元素</span><span class="sxs-lookup"><span data-stu-id="bc103-114">Parent Elements</span></span>

|<span data-ttu-id="bc103-115">項目</span><span class="sxs-lookup"><span data-stu-id="bc103-115">Element</span></span>|<span data-ttu-id="bc103-116">說明</span><span class="sxs-lookup"><span data-stu-id="bc103-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc103-117">TableControl 之 TableHeaders 的之 tablecolumnheader 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="bc103-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="bc103-118">定義資料表資料行的標籤、寬度和對齊方式。</span><span class="sxs-lookup"><span data-stu-id="bc103-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bc103-119">文字值</span><span class="sxs-lookup"><span data-stu-id="bc103-119">Text Value</span></span>

<span data-ttu-id="bc103-120">指定在資料表的資料行頂端顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="bc103-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="bc103-121">資料行標籤沒有受限制的字元。</span><span class="sxs-lookup"><span data-stu-id="bc103-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="bc103-122">備註</span><span class="sxs-lookup"><span data-stu-id="bc103-122">Remarks</span></span>

<span data-ttu-id="bc103-123">如果未指定任何標籤，則會使用其值顯示在資料列中的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="bc103-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="bc103-124">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="bc103-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="bc103-125">範例</span><span class="sxs-lookup"><span data-stu-id="bc103-125">Example</span></span>

<span data-ttu-id="bc103-126">這個範例會顯示其標籤為 "Column 1" 的 `TableColumnHeader` 元素。</span><span class="sxs-lookup"><span data-stu-id="bc103-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="bc103-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc103-127">See Also</span></span>

[<span data-ttu-id="bc103-128">建立資料表視圖</span><span class="sxs-lookup"><span data-stu-id="bc103-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="bc103-129">之 tablecolumnheader 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="bc103-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="bc103-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="bc103-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
