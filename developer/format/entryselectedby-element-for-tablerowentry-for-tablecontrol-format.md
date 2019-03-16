---
title: TableControl （格式） 的 TableRowEntry EntrySelectedBy 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058754"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="8dfaf-102">TableControl 之 TableRowEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8dfaf-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="8dfaf-103">定義使用此定義的資料表檢視或條件必須存在於要使用此定義的.NET 類型。</span><span class="sxs-lookup"><span data-stu-id="8dfaf-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="8dfaf-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 （格式） TableRowEntry 項目 （格式） EntrySelectedBy 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="8dfaf-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8dfaf-105">語法</span><span class="sxs-lookup"><span data-stu-id="8dfaf-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8dfaf-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="8dfaf-106">Attributes and Elements</span></span>

<span data-ttu-id="8dfaf-107">下列各節說明屬性、 子項目和父項目`EntrySelectedBy`項目。</span><span class="sxs-lookup"><span data-stu-id="8dfaf-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8dfaf-108">屬性</span><span class="sxs-lookup"><span data-stu-id="8dfaf-108">Attributes</span></span>

<span data-ttu-id="8dfaf-109">無。</span><span class="sxs-lookup"><span data-stu-id="8dfaf-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8dfaf-110">子元素</span><span class="sxs-lookup"><span data-stu-id="8dfaf-110">Child Elements</span></span>

|<span data-ttu-id="8dfaf-111">元素</span><span class="sxs-lookup"><span data-stu-id="8dfaf-111">Element</span></span>|<span data-ttu-id="8dfaf-112">描述</span><span class="sxs-lookup"><span data-stu-id="8dfaf-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8dfaf-113">TableControl （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="8dfaf-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="8dfaf-114">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="8dfaf-114">Optional element.</span></span><br /><br /> <span data-ttu-id="8dfaf-115">定義要使用此表格檢視定義必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="8dfaf-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="8dfaf-116">TableControl （格式） 的 EntrySelectedBy SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="8dfaf-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="8dfaf-117">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="8dfaf-117">Optional element.</span></span><br /><br /> <span data-ttu-id="8dfaf-118">指定一組使用這個資料表的檢視定義的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="8dfaf-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="8dfaf-119">TableControl （格式） 的 EntrySelectedBy TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="8dfaf-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="8dfaf-120">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="8dfaf-120">Optional element.</span></span><br /><br /> <span data-ttu-id="8dfaf-121">指定使用此資料表的檢視定義的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="8dfaf-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8dfaf-122">父元素</span><span class="sxs-lookup"><span data-stu-id="8dfaf-122">Parent Elements</span></span>

|<span data-ttu-id="8dfaf-123">元素</span><span class="sxs-lookup"><span data-stu-id="8dfaf-123">Element</span></span>|<span data-ttu-id="8dfaf-124">描述</span><span class="sxs-lookup"><span data-stu-id="8dfaf-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8dfaf-125">TableRowEntry TableControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="8dfaf-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="8dfaf-126">定義會顯示在資料表資料列的資料。</span><span class="sxs-lookup"><span data-stu-id="8dfaf-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8dfaf-127">備註</span><span class="sxs-lookup"><span data-stu-id="8dfaf-127">Remarks</span></span>

<span data-ttu-id="8dfaf-128">您必須指定至少一個型別、 選取項目集或資料表的檢視定義的選取範圍條件。</span><span class="sxs-lookup"><span data-stu-id="8dfaf-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="8dfaf-129">沒有任何子項目的，您可以使用數字的最大限制。</span><span class="sxs-lookup"><span data-stu-id="8dfaf-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="8dfaf-130">選擇條件用來定義要使用，例如當物件具有特定屬性的定義必須存在的條件，或特定的屬性值或指令碼會評估為`true`。</span><span class="sxs-lookup"><span data-stu-id="8dfaf-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="8dfaf-131">如需有關選擇條件的詳細資訊，請參閱[定義條件時檢視項目或項目用](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="8dfaf-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="8dfaf-132">資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="8dfaf-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8dfaf-133">範例</span><span class="sxs-lookup"><span data-stu-id="8dfaf-133">Example</span></span>

<span data-ttu-id="8dfaf-134">下列範例所示`TableRowEntry`用來顯示屬性的項目[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件。</span><span class="sxs-lookup"><span data-stu-id="8dfaf-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8dfaf-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8dfaf-135">See Also</span></span>

[<span data-ttu-id="8dfaf-136">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="8dfaf-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8dfaf-137">TableControl （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="8dfaf-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="8dfaf-138">TableControl （格式） 的 EntrySelectedBy SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="8dfaf-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="8dfaf-139">TableRowEntry TableControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="8dfaf-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="8dfaf-140">TableControl （格式） 的 EntrySelectedBy TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="8dfaf-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="8dfaf-141">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="8dfaf-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
