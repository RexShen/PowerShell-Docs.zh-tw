---
title: TableControl （格式） 的 TableColumnHeader 對齊項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067003"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="fab27-102">TableControl 之 TableColumnHeader 的對齊元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fab27-102">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="fab27-103">定義資料行標頭中的資料的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="fab27-103">Defines how the data in a column header is displayed.</span></span>

<span data-ttu-id="fab27-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableHeaders 項目 （格式） TableColumnHeader 項目 （格式） 對齊項目 TableColumnHeader （格式）</span><span class="sxs-lookup"><span data-stu-id="fab27-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element (Format) TableColumnHeader Element (Format) Alignment Element for TableColumnHeader (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fab27-105">語法</span><span class="sxs-lookup"><span data-stu-id="fab27-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fab27-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fab27-106">Attributes and Elements</span></span>

<span data-ttu-id="fab27-107">下列各節說明屬性、 子項目和父項目`Alignment`項目。</span><span class="sxs-lookup"><span data-stu-id="fab27-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fab27-108">屬性</span><span class="sxs-lookup"><span data-stu-id="fab27-108">Attributes</span></span>

<span data-ttu-id="fab27-109">無。</span><span class="sxs-lookup"><span data-stu-id="fab27-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fab27-110">子元素</span><span class="sxs-lookup"><span data-stu-id="fab27-110">Child Elements</span></span>

<span data-ttu-id="fab27-111">無。</span><span class="sxs-lookup"><span data-stu-id="fab27-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fab27-112">父項目</span><span class="sxs-lookup"><span data-stu-id="fab27-112">Parent Elements</span></span>

|<span data-ttu-id="fab27-113">項目</span><span class="sxs-lookup"><span data-stu-id="fab27-113">Element</span></span>|<span data-ttu-id="fab27-114">描述</span><span class="sxs-lookup"><span data-stu-id="fab27-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fab27-115">TableColumnHeader 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="fab27-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="fab27-116">定義標籤、 寬度和資料行的資料表資料的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="fab27-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fab27-117">文字值</span><span class="sxs-lookup"><span data-stu-id="fab27-117">Text Value</span></span>

<span data-ttu-id="fab27-118">指定下列值之一。</span><span class="sxs-lookup"><span data-stu-id="fab27-118">Specify one of the following values.</span></span> <span data-ttu-id="fab27-119">這些值不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="fab27-119">These values are not case-sensitive.</span></span>

<span data-ttu-id="fab27-120">如果未指定這個項目，這是預設值靠左對齊的資料顯示在左邊的資料行。</span><span class="sxs-lookup"><span data-stu-id="fab27-120">Left Aligns the data displayed in the column on the left This is the default if this element is not specified.</span></span>

<span data-ttu-id="fab27-121">靠右對齊顯示在右側資料行中的資料。</span><span class="sxs-lookup"><span data-stu-id="fab27-121">Right Aligns the data displayed in the column on the right.</span></span>

<span data-ttu-id="fab27-122">Center 中心資料行中顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="fab27-122">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="fab27-123">備註</span><span class="sxs-lookup"><span data-stu-id="fab27-123">Remarks</span></span>

<span data-ttu-id="fab27-124">資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="fab27-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fab27-125">範例</span><span class="sxs-lookup"><span data-stu-id="fab27-125">Example</span></span>

<span data-ttu-id="fab27-126">此範例示範`TableColumnHeader`其資料靠左項目。</span><span class="sxs-lookup"><span data-stu-id="fab27-126">This example shows a `TableColumnHeader` element whose data is aligned on the left.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="fab27-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fab27-127">See Also</span></span>

[<span data-ttu-id="fab27-128">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="fab27-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="fab27-129">TableColumnHeader 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="fab27-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="fab27-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="fab27-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
