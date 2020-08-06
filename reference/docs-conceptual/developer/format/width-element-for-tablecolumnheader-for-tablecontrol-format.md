---
title: TableControl (格式的之 tablecolumnheader 寬度元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e9540d3d351041ad7cb98a21bb360ebea7eca117
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779908"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="438dd-102">TableControl 之 TableColumnHeader 的寬度元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="438dd-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="438dd-103">定義資料行之字元) 的寬度 (。</span><span class="sxs-lookup"><span data-stu-id="438dd-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="438dd-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 專案 (格式) TableControl (格式) 之 tablecolumnheader 元素 TableHeaders 針對 TableControl (format) Width 元素之 tablecolumnheader (格式) </span><span class="sxs-lookup"><span data-stu-id="438dd-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="438dd-105">語法</span><span class="sxs-lookup"><span data-stu-id="438dd-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="438dd-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="438dd-106">Attributes and Elements</span></span>

<span data-ttu-id="438dd-107">下列各節說明定義資料行標頭時所使用之元素的屬性、子專案和父項目 `Width` 。</span><span class="sxs-lookup"><span data-stu-id="438dd-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="438dd-108">屬性</span><span class="sxs-lookup"><span data-stu-id="438dd-108">Attributes</span></span>

<span data-ttu-id="438dd-109">無。</span><span class="sxs-lookup"><span data-stu-id="438dd-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="438dd-110">子元素</span><span class="sxs-lookup"><span data-stu-id="438dd-110">Child Elements</span></span>

<span data-ttu-id="438dd-111">無。</span><span class="sxs-lookup"><span data-stu-id="438dd-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="438dd-112">父項目</span><span class="sxs-lookup"><span data-stu-id="438dd-112">Parent Elements</span></span>

|<span data-ttu-id="438dd-113">元素</span><span class="sxs-lookup"><span data-stu-id="438dd-113">Element</span></span>|<span data-ttu-id="438dd-114">描述</span><span class="sxs-lookup"><span data-stu-id="438dd-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="438dd-115">TableControl (格式的 TableHeaders 的之 tablecolumnheader 元素) </span><span class="sxs-lookup"><span data-stu-id="438dd-115">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="438dd-116">定義資料表資料行的標籤、寬度和對齊方式。</span><span class="sxs-lookup"><span data-stu-id="438dd-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="438dd-117">文字值</span><span class="sxs-lookup"><span data-stu-id="438dd-117">Text Value</span></span>

<span data-ttu-id="438dd-118">可能的話，請指定寬度 (字元) 大於顯示內容值的長度。</span><span class="sxs-lookup"><span data-stu-id="438dd-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="438dd-119">備註</span><span class="sxs-lookup"><span data-stu-id="438dd-119">Remarks</span></span>

<span data-ttu-id="438dd-120">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="438dd-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="438dd-121">範例</span><span class="sxs-lookup"><span data-stu-id="438dd-121">Example</span></span>

<span data-ttu-id="438dd-122">下列範例顯示 `TableColumnHeader` 其寬度為16個字元的元素。</span><span class="sxs-lookup"><span data-stu-id="438dd-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="438dd-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="438dd-123">See Also</span></span>

[<span data-ttu-id="438dd-124">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="438dd-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="438dd-125">TableControl (格式的 TableHeader 的之 tablecolumnheader 元素) </span><span class="sxs-lookup"><span data-stu-id="438dd-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="438dd-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="438dd-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
