---
title: TableControl （格式） 的 TableColumnItems TableColumnItem 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 5d80bdd736ad540f01c5ebc1f3d31dc9bd628ba5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862414"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="05d39-102">TableControl 之 TableColumnItems 的 TableColumnItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="05d39-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="05d39-103">定義屬性或其值會顯示在資料列的資料行的指令碼。</span><span class="sxs-lookup"><span data-stu-id="05d39-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="05d39-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 TableControl （格式） TableRowEntry TableRowEntries TableControl （格式） 的項目TableControl （格式） 的 TableColumnItems TableControl （格式） TableColumnItem 元素 TableControlEntry TableColumnItems 項目</span><span class="sxs-lookup"><span data-stu-id="05d39-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="05d39-105">語法</span><span class="sxs-lookup"><span data-stu-id="05d39-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <SciptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="05d39-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="05d39-106">Attributes and Elements</span></span>

<span data-ttu-id="05d39-107">下列各節說明屬性、 子項目和父項目`TableColumnItem`項目。</span><span class="sxs-lookup"><span data-stu-id="05d39-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="05d39-108">屬性</span><span class="sxs-lookup"><span data-stu-id="05d39-108">Attributes</span></span>

<span data-ttu-id="05d39-109">無。</span><span class="sxs-lookup"><span data-stu-id="05d39-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="05d39-110">子元素</span><span class="sxs-lookup"><span data-stu-id="05d39-110">Child Elements</span></span>

|<span data-ttu-id="05d39-111">元素</span><span class="sxs-lookup"><span data-stu-id="05d39-111">Element</span></span>|<span data-ttu-id="05d39-112">描述</span><span class="sxs-lookup"><span data-stu-id="05d39-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="05d39-113">TableControl （格式） 的 TableColumnItem 對齊項目</span><span class="sxs-lookup"><span data-stu-id="05d39-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="05d39-114">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="05d39-114">Optional element.</span></span><br /><br /> <span data-ttu-id="05d39-115">定義資料列的資料行中資料的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="05d39-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="05d39-116">TableControl （格式） 的 TableColumnItem 的 FormatString 元素</span><span class="sxs-lookup"><span data-stu-id="05d39-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="05d39-117">指定用來格式化資料列的資料行中資料的格式模式。</span><span class="sxs-lookup"><span data-stu-id="05d39-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="05d39-118">TableControl （格式） 的 TableColumnItem PropertyName 項目</span><span class="sxs-lookup"><span data-stu-id="05d39-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="05d39-119">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="05d39-119">Optional element.</span></span><br /><br /> <span data-ttu-id="05d39-120">指定其值會顯示屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="05d39-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="05d39-121">TableControl （格式） 的 TableColumnItem 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="05d39-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="05d39-122">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="05d39-122">Optional element.</span></span><br /><br /> <span data-ttu-id="05d39-123">指定其值會顯示一個資料列的資料行中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="05d39-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="05d39-124">父元素</span><span class="sxs-lookup"><span data-stu-id="05d39-124">Parent Elements</span></span>

|<span data-ttu-id="05d39-125">元素</span><span class="sxs-lookup"><span data-stu-id="05d39-125">Element</span></span>|<span data-ttu-id="05d39-126">描述</span><span class="sxs-lookup"><span data-stu-id="05d39-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="05d39-127">TableControl （格式） 的 TableControlEntry TableColumnItems 項目</span><span class="sxs-lookup"><span data-stu-id="05d39-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="05d39-128">定義屬性或其值會顯示資料列中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="05d39-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="05d39-129">備註</span><span class="sxs-lookup"><span data-stu-id="05d39-129">Remarks</span></span>

<span data-ttu-id="05d39-130">您可以指定屬性的物件或指令碼中的資料列的每個資料行。</span><span class="sxs-lookup"><span data-stu-id="05d39-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="05d39-131">如果未不指定任何子項目，項目是預留位置，並會顯示任何資料。</span><span class="sxs-lookup"><span data-stu-id="05d39-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="05d39-132">資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="05d39-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="05d39-133">範例</span><span class="sxs-lookup"><span data-stu-id="05d39-133">Example</span></span>

<span data-ttu-id="05d39-134">此範例示範`TableColumnItem`所顯示的值項目`Status`屬性[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件。</span><span class="sxs-lookup"><span data-stu-id="05d39-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="05d39-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05d39-135">See Also</span></span>

[<span data-ttu-id="05d39-136">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="05d39-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="05d39-137">TableControl （格式） 的 TableColumnItem 對齊項目</span><span class="sxs-lookup"><span data-stu-id="05d39-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="05d39-138">TableColumnItems 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="05d39-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="05d39-139">TableControl （格式） 的 TableColumnItem 的 FormatString 元素</span><span class="sxs-lookup"><span data-stu-id="05d39-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="05d39-140">TableControl （格式） 的 TableColumnItem PropertyName 項目</span><span class="sxs-lookup"><span data-stu-id="05d39-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="05d39-141">TableControl （格式） 的 TableColumnItem 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="05d39-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="05d39-142">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="05d39-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
