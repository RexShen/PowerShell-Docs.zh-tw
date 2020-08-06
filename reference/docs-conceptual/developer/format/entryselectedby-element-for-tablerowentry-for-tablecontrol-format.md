---
title: TableControl (格式) 的 TableRowEntry 的之 entryselectedby 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 047a10fb6b38dfa8f78a7741fd50b781d4a14b6d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787694"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="23c37-102">TableControl 之 TableRowEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="23c37-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="23c37-103">定義使用此資料表視圖定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="23c37-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="23c37-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) TableRowEntries 專案 (格式) TableRowEntry 專案 (格式) 之 entryselectedby 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="23c37-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="23c37-105">語法</span><span class="sxs-lookup"><span data-stu-id="23c37-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="23c37-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="23c37-106">Attributes and Elements</span></span>

<span data-ttu-id="23c37-107">下列各節說明屬性、子專案和元素的父元素 `EntrySelectedBy` 。</span><span class="sxs-lookup"><span data-stu-id="23c37-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="23c37-108">屬性</span><span class="sxs-lookup"><span data-stu-id="23c37-108">Attributes</span></span>

<span data-ttu-id="23c37-109">無。</span><span class="sxs-lookup"><span data-stu-id="23c37-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="23c37-110">子元素</span><span class="sxs-lookup"><span data-stu-id="23c37-110">Child Elements</span></span>

|<span data-ttu-id="23c37-111">元素</span><span class="sxs-lookup"><span data-stu-id="23c37-111">Element</span></span>|<span data-ttu-id="23c37-112">描述</span><span class="sxs-lookup"><span data-stu-id="23c37-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="23c37-113">TableControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="23c37-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="23c37-114">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="23c37-114">Optional element.</span></span><br /><br /> <span data-ttu-id="23c37-115">定義必須存在才能使用此資料表視圖定義的條件。</span><span class="sxs-lookup"><span data-stu-id="23c37-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="23c37-116">TableControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="23c37-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="23c37-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="23c37-117">Optional element.</span></span><br /><br /> <span data-ttu-id="23c37-118">指定一組使用此資料表視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="23c37-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="23c37-119">TableControl 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="23c37-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="23c37-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="23c37-120">Optional element.</span></span><br /><br /> <span data-ttu-id="23c37-121">指定使用此資料表視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="23c37-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="23c37-122">父項目</span><span class="sxs-lookup"><span data-stu-id="23c37-122">Parent Elements</span></span>

|<span data-ttu-id="23c37-123">元素</span><span class="sxs-lookup"><span data-stu-id="23c37-123">Element</span></span>|<span data-ttu-id="23c37-124">描述</span><span class="sxs-lookup"><span data-stu-id="23c37-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="23c37-125">TableControl (格式的 TableRowEntry 元素) </span><span class="sxs-lookup"><span data-stu-id="23c37-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="23c37-126">定義在資料表的資料列中顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="23c37-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="23c37-127">備註</span><span class="sxs-lookup"><span data-stu-id="23c37-127">Remarks</span></span>

<span data-ttu-id="23c37-128">您必須為數據表視圖定義指定至少一個類型、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="23c37-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="23c37-129">您可以使用的子項目數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="23c37-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="23c37-130">選取條件是用來定義要使用的定義必須存在的條件，例如，當物件具有特定屬性或特定屬性值或腳本評估為時 `true` 。</span><span class="sxs-lookup"><span data-stu-id="23c37-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="23c37-131">如需選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="23c37-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="23c37-132">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="23c37-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="23c37-133">範例</span><span class="sxs-lookup"><span data-stu-id="23c37-133">Example</span></span>

<span data-ttu-id="23c37-134">下列範例顯示 `TableRowEntry` 用來顯示 system.servicemodel [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件之屬性的專案。</span><span class="sxs-lookup"><span data-stu-id="23c37-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="23c37-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23c37-135">See Also</span></span>

[<span data-ttu-id="23c37-136">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="23c37-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="23c37-137">TableControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="23c37-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="23c37-138">TableControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="23c37-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="23c37-139">TableControl (格式的 TableRowEntry 元素) </span><span class="sxs-lookup"><span data-stu-id="23c37-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="23c37-140">TableControl 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="23c37-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="23c37-141">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="23c37-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
