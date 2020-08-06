---
title: TableControl 元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 34e20006a7501650f2a22f71a3d7e999fb8b2337
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785127"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="9c8bf-102">TableControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9c8bf-102">TableControl Element (Format)</span></span>

<span data-ttu-id="9c8bf-103">定義視圖的資料表格式。</span><span class="sxs-lookup"><span data-stu-id="9c8bf-103">Defines a table format for a view.</span></span>

<span data-ttu-id="9c8bf-104">ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="9c8bf-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9c8bf-105">語法</span><span class="sxs-lookup"><span data-stu-id="9c8bf-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="9c8bf-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9c8bf-106">Attributes and Elements</span></span>

<span data-ttu-id="9c8bf-107">下列各節描述元素的屬性、子專案和父項目 `TableControl` 。</span><span class="sxs-lookup"><span data-stu-id="9c8bf-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="9c8bf-108">您必須指定資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="9c8bf-108">You must specify the rows of the table.</span></span> <span data-ttu-id="9c8bf-109">所有其他子專案都是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="9c8bf-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="9c8bf-110">屬性</span><span class="sxs-lookup"><span data-stu-id="9c8bf-110">Attributes</span></span>

<span data-ttu-id="9c8bf-111">無。</span><span class="sxs-lookup"><span data-stu-id="9c8bf-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9c8bf-112">子元素</span><span class="sxs-lookup"><span data-stu-id="9c8bf-112">Child Elements</span></span>

|<span data-ttu-id="9c8bf-113">元素</span><span class="sxs-lookup"><span data-stu-id="9c8bf-113">Element</span></span>|<span data-ttu-id="9c8bf-114">描述</span><span class="sxs-lookup"><span data-stu-id="9c8bf-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9c8bf-115">TableControl 的 AutoSize 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9c8bf-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="9c8bf-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="9c8bf-116">Optional element.</span></span><br /><br /> <span data-ttu-id="9c8bf-117">指定是否根據資料大小來調整資料行大小和資料行數目。</span><span class="sxs-lookup"><span data-stu-id="9c8bf-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="9c8bf-118">TableControl (格式的 HideTableHeaders 元素) </span><span class="sxs-lookup"><span data-stu-id="9c8bf-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="9c8bf-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="9c8bf-119">Optional element.</span></span><br /><br /> <span data-ttu-id="9c8bf-120">指出是否不顯示資料表的標頭。</span><span class="sxs-lookup"><span data-stu-id="9c8bf-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="9c8bf-121">TableControl (格式的 TableHeaders 元素) </span><span class="sxs-lookup"><span data-stu-id="9c8bf-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="9c8bf-122">必要元素。</span><span class="sxs-lookup"><span data-stu-id="9c8bf-122">Required element.</span></span><br /><br /> <span data-ttu-id="9c8bf-123">定義資料表視圖之資料行的標籤、寬度和對齊方式。</span><span class="sxs-lookup"><span data-stu-id="9c8bf-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="9c8bf-124">TableControl 的 TableRowEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9c8bf-124">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="9c8bf-125">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="9c8bf-125">Optional element.</span></span><br /><br /> <span data-ttu-id="9c8bf-126">提供資料表視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="9c8bf-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9c8bf-127">父項目</span><span class="sxs-lookup"><span data-stu-id="9c8bf-127">Parent Elements</span></span>

|<span data-ttu-id="9c8bf-128">元素</span><span class="sxs-lookup"><span data-stu-id="9c8bf-128">Element</span></span>|<span data-ttu-id="9c8bf-129">描述</span><span class="sxs-lookup"><span data-stu-id="9c8bf-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9c8bf-130">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9c8bf-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="9c8bf-131">定義用來顯示一或多個物件成員的視圖。</span><span class="sxs-lookup"><span data-stu-id="9c8bf-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9c8bf-132">備註</span><span class="sxs-lookup"><span data-stu-id="9c8bf-132">Remarks</span></span>

<span data-ttu-id="9c8bf-133">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="9c8bf-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="9c8bf-134">範例</span><span class="sxs-lookup"><span data-stu-id="9c8bf-134">Example</span></span>

<span data-ttu-id="9c8bf-135">這個範例會示範 `TableControl` 用來顯示[Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件之屬性的元素。</span><span class="sxs-lookup"><span data-stu-id="9c8bf-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9c8bf-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c8bf-136">See Also</span></span>

[<span data-ttu-id="9c8bf-137">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="9c8bf-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="9c8bf-138">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9c8bf-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="9c8bf-139">TableControl 的 AutoSize 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9c8bf-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="9c8bf-140">HideTableHeaders 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9c8bf-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="9c8bf-141">TableHeaders 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9c8bf-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="9c8bf-142">TableRowEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="9c8bf-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="9c8bf-143">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="9c8bf-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
