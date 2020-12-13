---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 TableColumnItems 的 TableColumnItem 元素 (格式)
description: TableControl 之 TableColumnItems 的 TableColumnItem 元素 (格式)
ms.openlocfilehash: 8ef5158c9bb9f074d5c58190d4d3b20c10c83744
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659847"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="92136-103">TableControl 之 TableColumnItems 的 TableColumnItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="92136-103">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="92136-104">定義其值會顯示在資料列的資料行中的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="92136-104">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="92136-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) TableControl 元素 (format) TableRowEntries 元素 for TableControl (Format) TableRowEntry TableRowEntries for TableControl for TableColumnItems (format) TableControlEntry 元素 for TableControl for 之 tablecolumnitem (format) TableColumnItems 專案</span><span class="sxs-lookup"><span data-stu-id="92136-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="92136-106">語法</span><span class="sxs-lookup"><span data-stu-id="92136-106">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="92136-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="92136-107">Attributes and Elements</span></span>

<span data-ttu-id="92136-108">下列各節描述專案的屬性、子項目和父元素 `TableColumnItem` 。</span><span class="sxs-lookup"><span data-stu-id="92136-108">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="92136-109">屬性</span><span class="sxs-lookup"><span data-stu-id="92136-109">Attributes</span></span>

<span data-ttu-id="92136-110">無。</span><span class="sxs-lookup"><span data-stu-id="92136-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="92136-111">子元素</span><span class="sxs-lookup"><span data-stu-id="92136-111">Child Elements</span></span>

|<span data-ttu-id="92136-112">元素</span><span class="sxs-lookup"><span data-stu-id="92136-112">Element</span></span>|<span data-ttu-id="92136-113">描述</span><span class="sxs-lookup"><span data-stu-id="92136-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="92136-114">TableControl 之 TableColumnItem 的對齊元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="92136-114">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="92136-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="92136-115">Optional element.</span></span><br /><br /> <span data-ttu-id="92136-116">定義如何顯示資料列資料行中的資料。</span><span class="sxs-lookup"><span data-stu-id="92136-116">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="92136-117">TableControl 之 TableColumnItem 的 FormatString 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="92136-117">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="92136-118">指定格式模式，用來格式化資料列中資料行的資料。</span><span class="sxs-lookup"><span data-stu-id="92136-118">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="92136-119">TableControl 之 TableColumnItem 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="92136-119">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="92136-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="92136-120">Optional element.</span></span><br /><br /> <span data-ttu-id="92136-121">指定顯示其值的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="92136-121">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="92136-122">TableControl 之 TableColumnItem 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="92136-122">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="92136-123">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="92136-123">Optional element.</span></span><br /><br /> <span data-ttu-id="92136-124">指定其值會顯示在資料列的資料行中的腳本。</span><span class="sxs-lookup"><span data-stu-id="92136-124">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="92136-125">父項目</span><span class="sxs-lookup"><span data-stu-id="92136-125">Parent Elements</span></span>

|<span data-ttu-id="92136-126">元素</span><span class="sxs-lookup"><span data-stu-id="92136-126">Element</span></span>|<span data-ttu-id="92136-127">描述</span><span class="sxs-lookup"><span data-stu-id="92136-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="92136-128">適用于 TableControlEntry 的 TableControl (格式的 TableColumnItems 元素) </span><span class="sxs-lookup"><span data-stu-id="92136-128">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="92136-129">定義其值會顯示在資料列中的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="92136-129">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="92136-130">備註</span><span class="sxs-lookup"><span data-stu-id="92136-130">Remarks</span></span>

<span data-ttu-id="92136-131">您可以在資料列的每個資料行中指定物件或腳本的屬性。</span><span class="sxs-lookup"><span data-stu-id="92136-131">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="92136-132">如果未指定任何子項目，則專案為預留位置，且不會顯示任何資料。</span><span class="sxs-lookup"><span data-stu-id="92136-132">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="92136-133">如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="92136-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="92136-134">範例</span><span class="sxs-lookup"><span data-stu-id="92136-134">Example</span></span>

<span data-ttu-id="92136-135">這個範例顯示一個專案，這個專案 `TableColumnItem` 顯示 `Status` [system.object](/dotnet/api/System.Diagnostics.Process) 物件的屬性值。</span><span class="sxs-lookup"><span data-stu-id="92136-135">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="92136-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92136-136">See Also</span></span>

[<span data-ttu-id="92136-137">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="92136-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="92136-138">TableControl 之 TableColumnItem 的對齊元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="92136-138">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="92136-139">TableColumnItems 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="92136-139">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="92136-140">TableControl 之 TableColumnItem 的 FormatString 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="92136-140">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="92136-141">TableControl 之 TableColumnItem 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="92136-141">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="92136-142">TableControl 之 TableColumnItem 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="92136-142">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="92136-143">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="92136-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
