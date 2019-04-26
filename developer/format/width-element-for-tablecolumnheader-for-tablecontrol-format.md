---
title: TableControl （格式） 的 TableColumnHeader 的 width 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083615"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="d6e00-102">TableControl 之 TableColumnHeader 的寬度元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d6e00-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="d6e00-103">定義資料行的寬度 （以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="d6e00-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="d6e00-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableHeaders 項目 TableControl （格式） TableColumnHeader 元素 TableHeaders TableControl （格式） 的寬度元素TableControl （格式） 的 TableColumnHeader</span><span class="sxs-lookup"><span data-stu-id="d6e00-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d6e00-105">語法</span><span class="sxs-lookup"><span data-stu-id="d6e00-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d6e00-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d6e00-106">Attributes and Elements</span></span>

<span data-ttu-id="d6e00-107">下列各節說明屬性、 子項目和父項目`Width`定義資料行標頭時使用的項目。</span><span class="sxs-lookup"><span data-stu-id="d6e00-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="d6e00-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d6e00-108">Attributes</span></span>

<span data-ttu-id="d6e00-109">無。</span><span class="sxs-lookup"><span data-stu-id="d6e00-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d6e00-110">子元素</span><span class="sxs-lookup"><span data-stu-id="d6e00-110">Child Elements</span></span>

<span data-ttu-id="d6e00-111">無。</span><span class="sxs-lookup"><span data-stu-id="d6e00-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d6e00-112">父項目</span><span class="sxs-lookup"><span data-stu-id="d6e00-112">Parent Elements</span></span>

|<span data-ttu-id="d6e00-113">項目</span><span class="sxs-lookup"><span data-stu-id="d6e00-113">Element</span></span>|<span data-ttu-id="d6e00-114">描述</span><span class="sxs-lookup"><span data-stu-id="d6e00-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d6e00-115">TableControl （格式） 的 TableHeaders TableColumnHeader 項目</span><span class="sxs-lookup"><span data-stu-id="d6e00-115">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="d6e00-116">定義標籤、 寬度和對齊之資料行的資料表的資料。</span><span class="sxs-lookup"><span data-stu-id="d6e00-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d6e00-117">文字值</span><span class="sxs-lookup"><span data-stu-id="d6e00-117">Text Value</span></span>

<span data-ttu-id="d6e00-118">當在可能的話，指定顯示的屬性值的長度大於寬度 （以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="d6e00-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="d6e00-119">備註</span><span class="sxs-lookup"><span data-stu-id="d6e00-119">Remarks</span></span>

<span data-ttu-id="d6e00-120">資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d6e00-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d6e00-121">範例</span><span class="sxs-lookup"><span data-stu-id="d6e00-121">Example</span></span>

<span data-ttu-id="d6e00-122">下列範例所示`TableColumnHeader`寬度為 16 個字元的項目。</span><span class="sxs-lookup"><span data-stu-id="d6e00-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="d6e00-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6e00-123">See Also</span></span>

[<span data-ttu-id="d6e00-124">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="d6e00-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d6e00-125">TableControl （格式） 的 TableHeader TableColumnHeader 項目</span><span class="sxs-lookup"><span data-stu-id="d6e00-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="d6e00-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="d6e00-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
