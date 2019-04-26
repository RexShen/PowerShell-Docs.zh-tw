---
title: 供 TableColumnHeader 標籤項目，如 TableControl （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065745"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="92c62-102">TableControl 之 TableColumnHeader 的標籤元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="92c62-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="92c62-103">定義顯示在資料行頂端的標籤。</span><span class="sxs-lookup"><span data-stu-id="92c62-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="92c62-104">定義資料表的檢視時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="92c62-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="92c62-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableHeaders 項目 TableHeaders TableControl （格式） 的標籤元素的 TableControl （格式） TableColumnHeader 項目TableControl （格式） 的 TableColumnHeader</span><span class="sxs-lookup"><span data-stu-id="92c62-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="92c62-106">語法</span><span class="sxs-lookup"><span data-stu-id="92c62-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="92c62-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="92c62-107">Attributes and Elements</span></span>

<span data-ttu-id="92c62-108">下列各節說明屬性、 子項目和父項目`Label`項目。</span><span class="sxs-lookup"><span data-stu-id="92c62-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="92c62-109">每個資料行允許只有一個標籤。</span><span class="sxs-lookup"><span data-stu-id="92c62-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="92c62-110">屬性</span><span class="sxs-lookup"><span data-stu-id="92c62-110">Attributes</span></span>

<span data-ttu-id="92c62-111">無。</span><span class="sxs-lookup"><span data-stu-id="92c62-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="92c62-112">子元素</span><span class="sxs-lookup"><span data-stu-id="92c62-112">Child Elements</span></span>

<span data-ttu-id="92c62-113">無。</span><span class="sxs-lookup"><span data-stu-id="92c62-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="92c62-114">父項目</span><span class="sxs-lookup"><span data-stu-id="92c62-114">Parent Elements</span></span>

|<span data-ttu-id="92c62-115">項目</span><span class="sxs-lookup"><span data-stu-id="92c62-115">Element</span></span>|<span data-ttu-id="92c62-116">描述</span><span class="sxs-lookup"><span data-stu-id="92c62-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="92c62-117">TableControl （格式） 的 TableHeaders TableColumnHeader 項目</span><span class="sxs-lookup"><span data-stu-id="92c62-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="92c62-118">定義標籤、 寬度和資料行的資料表資料的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="92c62-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="92c62-119">文字值</span><span class="sxs-lookup"><span data-stu-id="92c62-119">Text Value</span></span>

<span data-ttu-id="92c62-120">指定顯示在資料表的資料行頂端的文字。</span><span class="sxs-lookup"><span data-stu-id="92c62-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="92c62-121">有任何限制的字元資料行標籤。</span><span class="sxs-lookup"><span data-stu-id="92c62-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="92c62-122">備註</span><span class="sxs-lookup"><span data-stu-id="92c62-122">Remarks</span></span>

<span data-ttu-id="92c62-123">如果未不指定任何標籤，會使用資料列中顯示其值之屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="92c62-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="92c62-124">資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="92c62-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="92c62-125">範例</span><span class="sxs-lookup"><span data-stu-id="92c62-125">Example</span></span>

<span data-ttu-id="92c62-126">此範例示範`TableColumnHeader`其標籤是 [資料行 1] 的項目。</span><span class="sxs-lookup"><span data-stu-id="92c62-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="92c62-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92c62-127">See Also</span></span>

[<span data-ttu-id="92c62-128">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="92c62-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="92c62-129">TableColumnHeader 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="92c62-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="92c62-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="92c62-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
