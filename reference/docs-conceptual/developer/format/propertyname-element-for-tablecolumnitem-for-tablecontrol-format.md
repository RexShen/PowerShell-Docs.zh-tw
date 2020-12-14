---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 TableColumnItem 的 PropertyName 元素 (格式)
description: TableControl 之 TableColumnItem 的 PropertyName 元素 (格式)
ms.openlocfilehash: e83bbdb96d2755013cb9fe065cb98731ba44917f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665578"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="1e558-103">TableControl 之 TableColumnItem 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1e558-103">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="1e558-104">指定其值會顯示在資料列的資料行中的屬性。</span><span class="sxs-lookup"><span data-stu-id="1e558-104">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="1e558-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) TableRowEntries 元素 (格式) TableRowEntry 專案 (格式) TableColumnItems 專案 (格式) 之 tablecolumnitem 專案 (格式) 之 tablecolumnitem (格式的 PropertyName 元素) </span><span class="sxs-lookup"><span data-stu-id="1e558-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1e558-106">語法</span><span class="sxs-lookup"><span data-stu-id="1e558-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1e558-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1e558-107">Attributes and Elements</span></span>

<span data-ttu-id="1e558-108">下列各節描述專案的屬性、子項目和父元素 `PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="1e558-108">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1e558-109">屬性</span><span class="sxs-lookup"><span data-stu-id="1e558-109">Attributes</span></span>

<span data-ttu-id="1e558-110">無。</span><span class="sxs-lookup"><span data-stu-id="1e558-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1e558-111">子元素</span><span class="sxs-lookup"><span data-stu-id="1e558-111">Child Elements</span></span>

<span data-ttu-id="1e558-112">無。</span><span class="sxs-lookup"><span data-stu-id="1e558-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1e558-113">父項目</span><span class="sxs-lookup"><span data-stu-id="1e558-113">Parent Elements</span></span>

|<span data-ttu-id="1e558-114">元素</span><span class="sxs-lookup"><span data-stu-id="1e558-114">Element</span></span>|<span data-ttu-id="1e558-115">描述</span><span class="sxs-lookup"><span data-stu-id="1e558-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1e558-116">之 tablecolumnitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="1e558-116">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="1e558-117">定義其值會顯示在資料列的資料行中的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="1e558-117">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1e558-118">文字值</span><span class="sxs-lookup"><span data-stu-id="1e558-118">Text Value</span></span>

<span data-ttu-id="1e558-119">指定顯示其值的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="1e558-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="1e558-120">備註</span><span class="sxs-lookup"><span data-stu-id="1e558-120">Remarks</span></span>

<span data-ttu-id="1e558-121">如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="1e558-121">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1e558-122">範例</span><span class="sxs-lookup"><span data-stu-id="1e558-122">Example</span></span>

<span data-ttu-id="1e558-123">這個範例顯示一個專案，這個專案 `TableColumnItem` 會指定 `Status` [system.object](/dotnet/api/System.Diagnostics.Process) 物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="1e558-123">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="1e558-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e558-124">See Also</span></span>

[<span data-ttu-id="1e558-125">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="1e558-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="1e558-126">之 tablecolumnitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="1e558-126">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="1e558-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="1e558-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
