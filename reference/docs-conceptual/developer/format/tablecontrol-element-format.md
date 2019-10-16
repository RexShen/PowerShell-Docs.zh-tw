---
title: TableControl 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368197"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="6dad0-102">TableControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="6dad0-102">TableControl Element (Format)</span></span>

<span data-ttu-id="6dad0-103">定義視圖的資料表格式。</span><span class="sxs-lookup"><span data-stu-id="6dad0-103">Defines a table format for a view.</span></span>

<span data-ttu-id="6dad0-104">ViewDefinitions 元素（格式） View 元素（Format） TableControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6dad0-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6dad0-105">語法</span><span class="sxs-lookup"><span data-stu-id="6dad0-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="6dad0-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="6dad0-106">Attributes and Elements</span></span>

<span data-ttu-id="6dad0-107">下列各節描述 `TableControl` 元素的屬性、子專案和父元素。</span><span class="sxs-lookup"><span data-stu-id="6dad0-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="6dad0-108">您必須指定資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="6dad0-108">You must specify the rows of the table.</span></span> <span data-ttu-id="6dad0-109">所有其他子專案都是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="6dad0-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="6dad0-110">屬性</span><span class="sxs-lookup"><span data-stu-id="6dad0-110">Attributes</span></span>

<span data-ttu-id="6dad0-111">無。</span><span class="sxs-lookup"><span data-stu-id="6dad0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6dad0-112">子元素</span><span class="sxs-lookup"><span data-stu-id="6dad0-112">Child Elements</span></span>

|<span data-ttu-id="6dad0-113">元素</span><span class="sxs-lookup"><span data-stu-id="6dad0-113">Element</span></span>|<span data-ttu-id="6dad0-114">描述</span><span class="sxs-lookup"><span data-stu-id="6dad0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6dad0-115">TableControl 的 AutoSize 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6dad0-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="6dad0-116">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="6dad0-116">Optional element.</span></span><br /><br /> <span data-ttu-id="6dad0-117">指定是否根據資料大小來調整資料行大小和資料行數目。</span><span class="sxs-lookup"><span data-stu-id="6dad0-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="6dad0-118">TableControl 的 HideTableHeaders 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6dad0-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="6dad0-119">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="6dad0-119">Optional element.</span></span><br /><br /> <span data-ttu-id="6dad0-120">指出是否不顯示資料表的標頭。</span><span class="sxs-lookup"><span data-stu-id="6dad0-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="6dad0-121">TableControl 的 TableHeaders 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6dad0-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="6dad0-122">必要元素。</span><span class="sxs-lookup"><span data-stu-id="6dad0-122">Required element.</span></span><br /><br /> <span data-ttu-id="6dad0-123">定義資料表視圖之資料行的標籤、寬度和對齊方式。</span><span class="sxs-lookup"><span data-stu-id="6dad0-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="6dad0-124">TableControl 的 TableRowEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6dad0-124">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="6dad0-125">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="6dad0-125">Optional element.</span></span><br /><br /> <span data-ttu-id="6dad0-126">提供資料表視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="6dad0-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6dad0-127">父元素</span><span class="sxs-lookup"><span data-stu-id="6dad0-127">Parent Elements</span></span>

|<span data-ttu-id="6dad0-128">元素</span><span class="sxs-lookup"><span data-stu-id="6dad0-128">Element</span></span>|<span data-ttu-id="6dad0-129">描述</span><span class="sxs-lookup"><span data-stu-id="6dad0-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6dad0-130">View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6dad0-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="6dad0-131">定義用來顯示一或多個物件成員的視圖。</span><span class="sxs-lookup"><span data-stu-id="6dad0-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6dad0-132">備註</span><span class="sxs-lookup"><span data-stu-id="6dad0-132">Remarks</span></span>

<span data-ttu-id="6dad0-133">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="6dad0-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6dad0-134">範例</span><span class="sxs-lookup"><span data-stu-id="6dad0-134">Example</span></span>

<span data-ttu-id="6dad0-135">這個範例會顯示一個用來顯示[system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件屬性的 @no__t 0 元素。</span><span class="sxs-lookup"><span data-stu-id="6dad0-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6dad0-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dad0-136">See Also</span></span>

[<span data-ttu-id="6dad0-137">建立資料表視圖</span><span class="sxs-lookup"><span data-stu-id="6dad0-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="6dad0-138">View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6dad0-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="6dad0-139">TableControl 的 AutoSize 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6dad0-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="6dad0-140">HideTableHeaders 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6dad0-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="6dad0-141">TableHeaders 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6dad0-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="6dad0-142">TableRowEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6dad0-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="6dad0-143">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="6dad0-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
