---
title: TableHeaders 元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b3176cbe1316d5b30cb61831d9915a80389709a5
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787422"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="7bc64-102">TableHeaders 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7bc64-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="7bc64-103">定義資料表之資料行的標頭。</span><span class="sxs-lookup"><span data-stu-id="7bc64-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="7bc64-104">ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) TableControl (格式的 TableHeaders 元素) </span><span class="sxs-lookup"><span data-stu-id="7bc64-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7bc64-105">語法</span><span class="sxs-lookup"><span data-stu-id="7bc64-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="7bc64-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7bc64-106">Attributes and Elements</span></span>

<span data-ttu-id="7bc64-107">下列各節描述元素的屬性、子專案和父項目 `TableHeaders` 。</span><span class="sxs-lookup"><span data-stu-id="7bc64-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="7bc64-108">要顯示之物件的每個屬性都必須要有一個子項目。</span><span class="sxs-lookup"><span data-stu-id="7bc64-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="7bc64-109">資料行標頭資訊會以指定子項目的順序顯示。</span><span class="sxs-lookup"><span data-stu-id="7bc64-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="7bc64-110">屬性</span><span class="sxs-lookup"><span data-stu-id="7bc64-110">Attributes</span></span>

<span data-ttu-id="7bc64-111">無。</span><span class="sxs-lookup"><span data-stu-id="7bc64-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7bc64-112">子元素</span><span class="sxs-lookup"><span data-stu-id="7bc64-112">Child Elements</span></span>

|<span data-ttu-id="7bc64-113">元素</span><span class="sxs-lookup"><span data-stu-id="7bc64-113">Element</span></span>|<span data-ttu-id="7bc64-114">描述</span><span class="sxs-lookup"><span data-stu-id="7bc64-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7bc64-115">TableColumnHeader 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7bc64-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="7bc64-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="7bc64-116">Optional element.</span></span><br /><br /> <span data-ttu-id="7bc64-117">定義資料表視圖之資料行的標籤、寬度和對齊方式。</span><span class="sxs-lookup"><span data-stu-id="7bc64-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7bc64-118">父項目</span><span class="sxs-lookup"><span data-stu-id="7bc64-118">Parent Elements</span></span>

|<span data-ttu-id="7bc64-119">元素</span><span class="sxs-lookup"><span data-stu-id="7bc64-119">Element</span></span>|<span data-ttu-id="7bc64-120">描述</span><span class="sxs-lookup"><span data-stu-id="7bc64-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7bc64-121">TableControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7bc64-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="7bc64-122">定義視圖的資料表格式。</span><span class="sxs-lookup"><span data-stu-id="7bc64-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7bc64-123">備註</span><span class="sxs-lookup"><span data-stu-id="7bc64-123">Remarks</span></span>

<span data-ttu-id="7bc64-124">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="7bc64-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7bc64-125">範例</span><span class="sxs-lookup"><span data-stu-id="7bc64-125">Example</span></span>

<span data-ttu-id="7bc64-126">這個範例會顯示 `TableHeaders` 定義兩個數據行標頭的元素。</span><span class="sxs-lookup"><span data-stu-id="7bc64-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
  <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a><span data-ttu-id="7bc64-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bc64-127">See Also</span></span>

[<span data-ttu-id="7bc64-128">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="7bc64-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="7bc64-129">TableColumnHeader 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7bc64-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="7bc64-130">TableControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7bc64-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="7bc64-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="7bc64-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
