---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 TableRowEntry 的 EntrySelectedBy 元素 (格式)
description: TableControl 之 TableRowEntry 的 EntrySelectedBy 元素 (格式)
ms.openlocfilehash: 1b7fc60b6fa9864b66e9edfebb3e4a86e287f3f8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645897"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="e6b47-103">TableControl 之 TableRowEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e6b47-103">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="e6b47-104">定義 .NET 型別，這些型別會使用資料表視圖的這個定義或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="e6b47-104">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="e6b47-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) TableControl 元素 (格式) TableRowEntries 元素 (格式) TableRowEntry 專案 (格式) 之 entryselectedby 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="e6b47-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e6b47-106">語法</span><span class="sxs-lookup"><span data-stu-id="e6b47-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e6b47-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e6b47-107">Attributes and Elements</span></span>

<span data-ttu-id="e6b47-108">下列各節說明屬性、子專案和元素的父元素 `EntrySelectedBy` 。</span><span class="sxs-lookup"><span data-stu-id="e6b47-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e6b47-109">屬性</span><span class="sxs-lookup"><span data-stu-id="e6b47-109">Attributes</span></span>

<span data-ttu-id="e6b47-110">無。</span><span class="sxs-lookup"><span data-stu-id="e6b47-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e6b47-111">子元素</span><span class="sxs-lookup"><span data-stu-id="e6b47-111">Child Elements</span></span>

|<span data-ttu-id="e6b47-112">元素</span><span class="sxs-lookup"><span data-stu-id="e6b47-112">Element</span></span>|<span data-ttu-id="e6b47-113">描述</span><span class="sxs-lookup"><span data-stu-id="e6b47-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e6b47-114">TableControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e6b47-114">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="e6b47-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e6b47-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e6b47-116">定義必須存在的條件，才能使用此資料表視圖定義。</span><span class="sxs-lookup"><span data-stu-id="e6b47-116">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="e6b47-117">TableControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e6b47-117">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="e6b47-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e6b47-118">Optional element.</span></span><br /><br /> <span data-ttu-id="e6b47-119">指定一組使用此資料表視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="e6b47-119">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="e6b47-120">TableControl 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e6b47-120">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="e6b47-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e6b47-121">Optional element.</span></span><br /><br /> <span data-ttu-id="e6b47-122">指定使用此資料表視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="e6b47-122">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e6b47-123">父項目</span><span class="sxs-lookup"><span data-stu-id="e6b47-123">Parent Elements</span></span>

|<span data-ttu-id="e6b47-124">元素</span><span class="sxs-lookup"><span data-stu-id="e6b47-124">Element</span></span>|<span data-ttu-id="e6b47-125">描述</span><span class="sxs-lookup"><span data-stu-id="e6b47-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e6b47-126">TableControl (格式的 TableRowEntry 元素) </span><span class="sxs-lookup"><span data-stu-id="e6b47-126">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="e6b47-127">定義顯示在資料表資料列中的資料。</span><span class="sxs-lookup"><span data-stu-id="e6b47-127">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e6b47-128">備註</span><span class="sxs-lookup"><span data-stu-id="e6b47-128">Remarks</span></span>

<span data-ttu-id="e6b47-129">您必須為數據表視圖定義指定至少一個類型、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="e6b47-129">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="e6b47-130">您可以使用的子項目數目沒有最大限制。</span><span class="sxs-lookup"><span data-stu-id="e6b47-130">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="e6b47-131">選取條件是用來定義必須存在才能使用定義的條件，例如，當物件具有特定屬性或特定屬性值或腳本評估為時 `true` 。</span><span class="sxs-lookup"><span data-stu-id="e6b47-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="e6b47-132">如需選取條件的詳細資訊，請參閱 [定義使用視圖專案或專案的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e6b47-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e6b47-133">如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="e6b47-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e6b47-134">範例</span><span class="sxs-lookup"><span data-stu-id="e6b47-134">Example</span></span>

<span data-ttu-id="e6b47-135">下列範例 `TableRowEntry` 會顯示用來顯示 system.string [](/dotnet/api/System.Diagnostics.Process)物件屬性的專案。</span><span class="sxs-lookup"><span data-stu-id="e6b47-135">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a><span data-ttu-id="e6b47-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6b47-136">See Also</span></span>

[<span data-ttu-id="e6b47-137">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="e6b47-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e6b47-138">TableControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e6b47-138">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e6b47-139">TableControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e6b47-139">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e6b47-140">TableControl (格式的 TableRowEntry 元素) </span><span class="sxs-lookup"><span data-stu-id="e6b47-140">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="e6b47-141">TableControl 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e6b47-141">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e6b47-142">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="e6b47-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
