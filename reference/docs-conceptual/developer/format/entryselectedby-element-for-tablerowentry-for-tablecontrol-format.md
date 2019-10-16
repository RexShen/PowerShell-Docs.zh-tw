---
title: TableControl 之 TableRowEntry 的之 entryselectedby 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363337"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="9a529-102">TableControl 之 TableRowEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9a529-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="9a529-103">定義使用此資料表視圖定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="9a529-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="9a529-104">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（格式） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（格式）之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9a529-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9a529-105">語法</span><span class="sxs-lookup"><span data-stu-id="9a529-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9a529-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="9a529-106">Attributes and Elements</span></span>

<span data-ttu-id="9a529-107">下列各節說明屬性、子專案，以及 `EntrySelectedBy` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="9a529-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9a529-108">屬性</span><span class="sxs-lookup"><span data-stu-id="9a529-108">Attributes</span></span>

<span data-ttu-id="9a529-109">無。</span><span class="sxs-lookup"><span data-stu-id="9a529-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9a529-110">子元素</span><span class="sxs-lookup"><span data-stu-id="9a529-110">Child Elements</span></span>

|<span data-ttu-id="9a529-111">元素</span><span class="sxs-lookup"><span data-stu-id="9a529-111">Element</span></span>|<span data-ttu-id="9a529-112">描述</span><span class="sxs-lookup"><span data-stu-id="9a529-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9a529-113">TableControl 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9a529-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="9a529-114">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="9a529-114">Optional element.</span></span><br /><br /> <span data-ttu-id="9a529-115">定義必須存在才能使用此資料表視圖定義的條件。</span><span class="sxs-lookup"><span data-stu-id="9a529-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="9a529-116">TableControl 之之 entryselectedby 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9a529-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="9a529-117">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="9a529-117">Optional element.</span></span><br /><br /> <span data-ttu-id="9a529-118">指定一組使用此資料表視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="9a529-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="9a529-119">TableControl 之之 entryselectedby 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9a529-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="9a529-120">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="9a529-120">Optional element.</span></span><br /><br /> <span data-ttu-id="9a529-121">指定使用此資料表視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="9a529-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9a529-122">父元素</span><span class="sxs-lookup"><span data-stu-id="9a529-122">Parent Elements</span></span>

|<span data-ttu-id="9a529-123">元素</span><span class="sxs-lookup"><span data-stu-id="9a529-123">Element</span></span>|<span data-ttu-id="9a529-124">描述</span><span class="sxs-lookup"><span data-stu-id="9a529-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9a529-125">TableControl 的 TableRowEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9a529-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="9a529-126">定義在資料表的資料列中顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="9a529-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9a529-127">備註</span><span class="sxs-lookup"><span data-stu-id="9a529-127">Remarks</span></span>

<span data-ttu-id="9a529-128">您必須為數據表視圖定義指定至少一個類型、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="9a529-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="9a529-129">您可以使用的子項目數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="9a529-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="9a529-130">選取條件是用來定義要使用的定義必須存在的條件，例如，當物件具有特定屬性，或特定屬性值或腳本評估為 `true` 時。</span><span class="sxs-lookup"><span data-stu-id="9a529-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="9a529-131">如需選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="9a529-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="9a529-132">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="9a529-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="9a529-133">範例</span><span class="sxs-lookup"><span data-stu-id="9a529-133">Example</span></span>

<span data-ttu-id="9a529-134">下列範例顯示用來顯示[system.servicemodel 物件屬性](/dotnet/api/System.Diagnostics.Process)的 `TableRowEntry` 元素：。</span><span class="sxs-lookup"><span data-stu-id="9a529-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9a529-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a529-135">See Also</span></span>

[<span data-ttu-id="9a529-136">建立資料表視圖</span><span class="sxs-lookup"><span data-stu-id="9a529-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="9a529-137">TableControl 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9a529-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="9a529-138">TableControl 之之 entryselectedby 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9a529-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="9a529-139">TableControl 的 TableRowEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9a529-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="9a529-140">TableControl 之之 entryselectedby 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9a529-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="9a529-141">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="9a529-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
