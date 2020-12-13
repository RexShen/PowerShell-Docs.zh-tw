---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 元素 (格式)
description: TableControl 元素 (格式)
ms.openlocfilehash: 93e05e22d61504d7781b6f3c07f9a3fd0b3c9e8a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651452"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="732d9-103">TableControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="732d9-103">TableControl Element (Format)</span></span>

<span data-ttu-id="732d9-104">定義視圖的資料表格式。</span><span class="sxs-lookup"><span data-stu-id="732d9-104">Defines a table format for a view.</span></span>

<span data-ttu-id="732d9-105">ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="732d9-105">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="732d9-106">語法</span><span class="sxs-lookup"><span data-stu-id="732d9-106">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="732d9-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="732d9-107">Attributes and Elements</span></span>

<span data-ttu-id="732d9-108">下列各節描述專案的屬性、子項目和父元素 `TableControl` 。</span><span class="sxs-lookup"><span data-stu-id="732d9-108">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="732d9-109">您必須指定資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="732d9-109">You must specify the rows of the table.</span></span> <span data-ttu-id="732d9-110">所有其他子項目都是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="732d9-110">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="732d9-111">屬性</span><span class="sxs-lookup"><span data-stu-id="732d9-111">Attributes</span></span>

<span data-ttu-id="732d9-112">無。</span><span class="sxs-lookup"><span data-stu-id="732d9-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="732d9-113">子元素</span><span class="sxs-lookup"><span data-stu-id="732d9-113">Child Elements</span></span>

|<span data-ttu-id="732d9-114">元素</span><span class="sxs-lookup"><span data-stu-id="732d9-114">Element</span></span>|<span data-ttu-id="732d9-115">描述</span><span class="sxs-lookup"><span data-stu-id="732d9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="732d9-116">TableControl 的 AutoSize 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="732d9-116">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="732d9-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="732d9-117">Optional element.</span></span><br /><br /> <span data-ttu-id="732d9-118">指定是否根據資料的大小調整資料行大小和資料行數目。</span><span class="sxs-lookup"><span data-stu-id="732d9-118">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="732d9-119">TableControl (格式的 HideTableHeaders 元素) </span><span class="sxs-lookup"><span data-stu-id="732d9-119">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="732d9-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="732d9-120">Optional element.</span></span><br /><br /> <span data-ttu-id="732d9-121">指出是否不顯示資料表的標頭。</span><span class="sxs-lookup"><span data-stu-id="732d9-121">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="732d9-122">TableControl (格式的 TableHeaders 元素) </span><span class="sxs-lookup"><span data-stu-id="732d9-122">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="732d9-123">必要元素。</span><span class="sxs-lookup"><span data-stu-id="732d9-123">Required element.</span></span><br /><br /> <span data-ttu-id="732d9-124">定義資料表視圖之資料行的標籤、寬度和對齊方式。</span><span class="sxs-lookup"><span data-stu-id="732d9-124">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="732d9-125">TableControl 的 TableRowEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="732d9-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="732d9-126">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="732d9-126">Optional element.</span></span><br /><br /> <span data-ttu-id="732d9-127">提供資料表視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="732d9-127">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="732d9-128">父項目</span><span class="sxs-lookup"><span data-stu-id="732d9-128">Parent Elements</span></span>

|<span data-ttu-id="732d9-129">元素</span><span class="sxs-lookup"><span data-stu-id="732d9-129">Element</span></span>|<span data-ttu-id="732d9-130">描述</span><span class="sxs-lookup"><span data-stu-id="732d9-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="732d9-131">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="732d9-131">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="732d9-132">定義用來顯示一或多個物件成員的視圖。</span><span class="sxs-lookup"><span data-stu-id="732d9-132">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="732d9-133">備註</span><span class="sxs-lookup"><span data-stu-id="732d9-133">Remarks</span></span>

<span data-ttu-id="732d9-134">如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="732d9-134">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="732d9-135">範例</span><span class="sxs-lookup"><span data-stu-id="732d9-135">Example</span></span>

<span data-ttu-id="732d9-136">此範例顯示 `TableControl` 用來顯示 [system.serviceprocess.dll Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 物件屬性的元素。</span><span class="sxs-lookup"><span data-stu-id="732d9-136">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="732d9-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="732d9-137">See Also</span></span>

[<span data-ttu-id="732d9-138">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="732d9-138">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="732d9-139">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="732d9-139">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="732d9-140">TableControl 的 AutoSize 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="732d9-140">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="732d9-141">HideTableHeaders 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="732d9-141">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="732d9-142">TableHeaders 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="732d9-142">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="732d9-143">TableRowEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="732d9-143">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="732d9-144">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="732d9-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
