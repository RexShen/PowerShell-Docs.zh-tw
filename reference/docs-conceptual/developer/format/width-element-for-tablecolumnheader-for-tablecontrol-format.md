---
title: TableControl 之之 tablecolumnheader 的 Width 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367867"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="b7d32-102">TableControl 之 TableColumnHeader 的寬度元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b7d32-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="b7d32-103">定義資料行的寬度（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="b7d32-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="b7d32-104">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（format） TableHeaders 元素（適用于之 tablecolumnheader （Format））的 TableControl （格式） TableHeaders 元素 TableControlTableControl 的之 tablecolumnheader （格式）</span><span class="sxs-lookup"><span data-stu-id="b7d32-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b7d32-105">語法</span><span class="sxs-lookup"><span data-stu-id="b7d32-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b7d32-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="b7d32-106">Attributes and Elements</span></span>

<span data-ttu-id="b7d32-107">下列各節描述定義資料行標頭時所使用之 `Width` 元素的屬性、子專案和父項目。</span><span class="sxs-lookup"><span data-stu-id="b7d32-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="b7d32-108">屬性</span><span class="sxs-lookup"><span data-stu-id="b7d32-108">Attributes</span></span>

<span data-ttu-id="b7d32-109">無。</span><span class="sxs-lookup"><span data-stu-id="b7d32-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b7d32-110">子元素</span><span class="sxs-lookup"><span data-stu-id="b7d32-110">Child Elements</span></span>

<span data-ttu-id="b7d32-111">無。</span><span class="sxs-lookup"><span data-stu-id="b7d32-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b7d32-112">父元素</span><span class="sxs-lookup"><span data-stu-id="b7d32-112">Parent Elements</span></span>

|<span data-ttu-id="b7d32-113">元素</span><span class="sxs-lookup"><span data-stu-id="b7d32-113">Element</span></span>|<span data-ttu-id="b7d32-114">描述</span><span class="sxs-lookup"><span data-stu-id="b7d32-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7d32-115">TableControl 之 TableHeaders 的之 tablecolumnheader 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7d32-115">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="b7d32-116">定義資料表資料行的標籤、寬度和對齊方式。</span><span class="sxs-lookup"><span data-stu-id="b7d32-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b7d32-117">文字值</span><span class="sxs-lookup"><span data-stu-id="b7d32-117">Text Value</span></span>

<span data-ttu-id="b7d32-118">可能的話，請指定大於所顯示內容值長度的寬度（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="b7d32-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="b7d32-119">備註</span><span class="sxs-lookup"><span data-stu-id="b7d32-119">Remarks</span></span>

<span data-ttu-id="b7d32-120">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="b7d32-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b7d32-121">範例</span><span class="sxs-lookup"><span data-stu-id="b7d32-121">Example</span></span>

<span data-ttu-id="b7d32-122">下列範例會顯示其寬度為16個字元的 `TableColumnHeader` 元素。</span><span class="sxs-lookup"><span data-stu-id="b7d32-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="b7d32-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7d32-123">See Also</span></span>

[<span data-ttu-id="b7d32-124">建立資料表視圖</span><span class="sxs-lookup"><span data-stu-id="b7d32-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b7d32-125">TableControl 之 TableHeader 的之 tablecolumnheader 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7d32-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="b7d32-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="b7d32-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
