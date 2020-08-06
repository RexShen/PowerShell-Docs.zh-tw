---
title: TableControl (格式) 的 TableColumnItems 的之 tablecolumnitem 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: beadf771f02519394d799a03db374050e3302321
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785161"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="83453-102">TableControl 之 TableColumnItems 的 TableColumnItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="83453-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="83453-103">定義屬性或腳本，其值會顯示在資料列的資料行中。</span><span class="sxs-lookup"><span data-stu-id="83453-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="83453-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 專案 (格式) TableControl (Format) TableRowEntry 元素（TableRowEntries for TableControl 的 TableColumnItems (format) TableControlEntry 元素，TableControl for 之 tablecolumnitem (format) TableColumnItems 專案 (</span><span class="sxs-lookup"><span data-stu-id="83453-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="83453-105">語法</span><span class="sxs-lookup"><span data-stu-id="83453-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="83453-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="83453-106">Attributes and Elements</span></span>

<span data-ttu-id="83453-107">下列各節描述元素的屬性、子專案和父項目 `TableColumnItem` 。</span><span class="sxs-lookup"><span data-stu-id="83453-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="83453-108">屬性</span><span class="sxs-lookup"><span data-stu-id="83453-108">Attributes</span></span>

<span data-ttu-id="83453-109">無。</span><span class="sxs-lookup"><span data-stu-id="83453-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="83453-110">子元素</span><span class="sxs-lookup"><span data-stu-id="83453-110">Child Elements</span></span>

|<span data-ttu-id="83453-111">元素</span><span class="sxs-lookup"><span data-stu-id="83453-111">Element</span></span>|<span data-ttu-id="83453-112">描述</span><span class="sxs-lookup"><span data-stu-id="83453-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="83453-113">TableControl 之 TableColumnItem 的對齊元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="83453-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="83453-114">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="83453-114">Optional element.</span></span><br /><br /> <span data-ttu-id="83453-115">定義如何顯示資料列資料行中的資料。</span><span class="sxs-lookup"><span data-stu-id="83453-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="83453-116">TableControl 之 TableColumnItem 的 FormatString 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="83453-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="83453-117">指定格式模式，用來格式化資料列之資料行中的資料。</span><span class="sxs-lookup"><span data-stu-id="83453-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="83453-118">TableControl 之 TableColumnItem 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="83453-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="83453-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="83453-119">Optional element.</span></span><br /><br /> <span data-ttu-id="83453-120">指定顯示其值的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="83453-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="83453-121">TableControl 之 TableColumnItem 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="83453-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="83453-122">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="83453-122">Optional element.</span></span><br /><br /> <span data-ttu-id="83453-123">指定其值顯示在資料列資料行中的腳本。</span><span class="sxs-lookup"><span data-stu-id="83453-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="83453-124">父項目</span><span class="sxs-lookup"><span data-stu-id="83453-124">Parent Elements</span></span>

|<span data-ttu-id="83453-125">元素</span><span class="sxs-lookup"><span data-stu-id="83453-125">Element</span></span>|<span data-ttu-id="83453-126">描述</span><span class="sxs-lookup"><span data-stu-id="83453-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="83453-127">TableControl (格式的 TableControlEntry 的 TableColumnItems 元素) </span><span class="sxs-lookup"><span data-stu-id="83453-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="83453-128">定義其值會顯示在資料列中的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="83453-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="83453-129">備註</span><span class="sxs-lookup"><span data-stu-id="83453-129">Remarks</span></span>

<span data-ttu-id="83453-130">您可以在資料列的每個資料行中指定物件的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="83453-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="83453-131">如果未指定任何子項目，則專案為預留位置，而且不會顯示任何資料。</span><span class="sxs-lookup"><span data-stu-id="83453-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="83453-132">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="83453-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="83453-133">範例</span><span class="sxs-lookup"><span data-stu-id="83453-133">Example</span></span>

<span data-ttu-id="83453-134">這個範例會顯示一個專案 `TableColumnItem` ，該專案會顯示 `Status` [system.webserver](/dotnet/api/System.Diagnostics.Process)物件的屬性值。</span><span class="sxs-lookup"><span data-stu-id="83453-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="83453-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83453-135">See Also</span></span>

[<span data-ttu-id="83453-136">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="83453-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="83453-137">TableControl 之 TableColumnItem 的對齊元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="83453-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="83453-138">TableColumnItems 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="83453-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="83453-139">TableControl 之 TableColumnItem 的 FormatString 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="83453-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="83453-140">TableControl 之 TableColumnItem 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="83453-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="83453-141">TableControl 之 TableColumnItem 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="83453-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="83453-142">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="83453-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
