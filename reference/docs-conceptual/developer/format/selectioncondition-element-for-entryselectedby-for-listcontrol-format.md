---
title: ListControl (格式) 的之 entryselectedby 的 SelectionCondition 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 29626b181f21d168e1ebf973e01afeb411d9ef54
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772768"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="57ae8-102">ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="57ae8-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="57ae8-103">定義必須存在才能使用此清單視圖定義的條件。</span><span class="sxs-lookup"><span data-stu-id="57ae8-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="57ae8-104">可以為清單定義指定的選取條件數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="57ae8-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="57ae8-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListEntries 專案 (格式) ListEntry 專案 (格式) 之 entryselectedby 元素用於 ListEntry (格式) SelectionCondition 元素 (</span><span class="sxs-lookup"><span data-stu-id="57ae8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="57ae8-106">語法</span><span class="sxs-lookup"><span data-stu-id="57ae8-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="57ae8-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="57ae8-107">Attributes and Elements</span></span>

<span data-ttu-id="57ae8-108">下列各節說明屬性、子專案和元素的父元素 `SelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="57ae8-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="57ae8-109">屬性</span><span class="sxs-lookup"><span data-stu-id="57ae8-109">Attributes</span></span>

<span data-ttu-id="57ae8-110">無。</span><span class="sxs-lookup"><span data-stu-id="57ae8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="57ae8-111">子元素</span><span class="sxs-lookup"><span data-stu-id="57ae8-111">Child Elements</span></span>

|<span data-ttu-id="57ae8-112">元素</span><span class="sxs-lookup"><span data-stu-id="57ae8-112">Element</span></span>|<span data-ttu-id="57ae8-113">描述</span><span class="sxs-lookup"><span data-stu-id="57ae8-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="57ae8-114">SelectionCondition for 之 entryselectedby for ListEntry (Format 的 PropertyName 元素) </span><span class="sxs-lookup"><span data-stu-id="57ae8-114">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="57ae8-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="57ae8-115">Optional element.</span></span><br /><br /> <span data-ttu-id="57ae8-116">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="57ae8-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="57ae8-117">SelectionCondition for 之 entryselectedby for ListEntry (Format 的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="57ae8-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="57ae8-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="57ae8-118">Optional element.</span></span><br /><br /> <span data-ttu-id="57ae8-119">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="57ae8-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="57ae8-120">ListEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="57ae8-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="57ae8-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="57ae8-121">Optional element.</span></span><br /><br /> <span data-ttu-id="57ae8-122">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="57ae8-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="57ae8-123">SelectionCondition for 之 entryselectedby for ListEntry (Format 的 TypeName 元素) </span><span class="sxs-lookup"><span data-stu-id="57ae8-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="57ae8-124">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="57ae8-124">Optional element.</span></span><br /><br /> <span data-ttu-id="57ae8-125">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="57ae8-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="57ae8-126">父項目</span><span class="sxs-lookup"><span data-stu-id="57ae8-126">Parent Elements</span></span>

|<span data-ttu-id="57ae8-127">元素</span><span class="sxs-lookup"><span data-stu-id="57ae8-127">Element</span></span>|<span data-ttu-id="57ae8-128">描述</span><span class="sxs-lookup"><span data-stu-id="57ae8-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="57ae8-129">TableRowEntry (格式的之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="57ae8-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="57ae8-130">定義使用此資料表專案的 .NET 類型，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="57ae8-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="57ae8-131">備註</span><span class="sxs-lookup"><span data-stu-id="57ae8-131">Remarks</span></span>

<span data-ttu-id="57ae8-132">lWhen 您定義選取條件時，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="57ae8-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="57ae8-133">選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="57ae8-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="57ae8-134">選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="57ae8-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="57ae8-135">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="57ae8-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="57ae8-136">如需清單視圖之其他元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="57ae8-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="57ae8-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57ae8-137">See Also</span></span>

[<span data-ttu-id="57ae8-138">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="57ae8-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="57ae8-139">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="57ae8-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="57ae8-140">ListEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="57ae8-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="57ae8-141">ListEntry (格式的之 entryselectedby 的 SelectionSetName 元素) </span><span class="sxs-lookup"><span data-stu-id="57ae8-141">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="57ae8-142">之 entryselectedby for ListEntry (格式的 TypeName 元素) </span><span class="sxs-lookup"><span data-stu-id="57ae8-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](/powershell/scripting/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[<span data-ttu-id="57ae8-143">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="57ae8-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
