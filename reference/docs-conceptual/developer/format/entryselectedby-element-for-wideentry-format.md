---
ms.date: 09/13/2016
ms.topic: reference
title: WideEntry 的 EntrySelectedBy 元素 (格式)
description: WideEntry 的 EntrySelectedBy 元素 (格式)
ms.openlocfilehash: 246a1967300ab0551f376c4799deac275068308c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660247"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="c91f5-103">WideEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c91f5-103">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="c91f5-104">定義 .NET 型別，這些型別會使用此寬視圖的定義或必須存在的條件，才能使用這個定義。</span><span class="sxs-lookup"><span data-stu-id="c91f5-104">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="c91f5-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) WideControl 元素 (format) WideEntries 元素 (format) WideEntry 專案 (格式) 之 entryselectedby 專案的 WideEntry (格式) </span><span class="sxs-lookup"><span data-stu-id="c91f5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c91f5-106">語法</span><span class="sxs-lookup"><span data-stu-id="c91f5-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c91f5-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c91f5-107">Attributes and Elements</span></span>

<span data-ttu-id="c91f5-108">下列各節說明屬性、子專案和元素的父元素 `EntrySelectedBy` 。</span><span class="sxs-lookup"><span data-stu-id="c91f5-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c91f5-109">屬性</span><span class="sxs-lookup"><span data-stu-id="c91f5-109">Attributes</span></span>

<span data-ttu-id="c91f5-110">無。</span><span class="sxs-lookup"><span data-stu-id="c91f5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c91f5-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c91f5-111">Child Elements</span></span>

|<span data-ttu-id="c91f5-112">元素</span><span class="sxs-lookup"><span data-stu-id="c91f5-112">Element</span></span>|<span data-ttu-id="c91f5-113">描述</span><span class="sxs-lookup"><span data-stu-id="c91f5-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c91f5-114">適用于之 entryselectedby 的 WideEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="c91f5-114">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="c91f5-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="c91f5-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c91f5-116">定義必須存在的條件，才能使用此寬視圖定義。</span><span class="sxs-lookup"><span data-stu-id="c91f5-116">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="c91f5-117">適用于之 entryselectedby 的 WideEntry (格式的 SelectionSetName 元素) </span><span class="sxs-lookup"><span data-stu-id="c91f5-117">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="c91f5-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="c91f5-118">Optional element.</span></span><br /><br /> <span data-ttu-id="c91f5-119">指定一組使用此廣泛視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="c91f5-119">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="c91f5-120">WideEntry 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c91f5-120">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="c91f5-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="c91f5-121">Optional element.</span></span><br /><br /> <span data-ttu-id="c91f5-122">指定使用此廣泛視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="c91f5-122">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c91f5-123">父項目</span><span class="sxs-lookup"><span data-stu-id="c91f5-123">Parent Elements</span></span>

|<span data-ttu-id="c91f5-124">元素</span><span class="sxs-lookup"><span data-stu-id="c91f5-124">Element</span></span>|<span data-ttu-id="c91f5-125">描述</span><span class="sxs-lookup"><span data-stu-id="c91f5-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c91f5-126">WideEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="c91f5-126">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="c91f5-127">提供寬視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="c91f5-127">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c91f5-128">備註</span><span class="sxs-lookup"><span data-stu-id="c91f5-128">Remarks</span></span>

<span data-ttu-id="c91f5-129">您必須為寬視圖定義指定至少一個類型、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="c91f5-129">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="c91f5-130">您可以使用的子項目數目沒有最大限制。</span><span class="sxs-lookup"><span data-stu-id="c91f5-130">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="c91f5-131">選取條件是用來定義必須存在才能使用定義的條件，例如，當物件具有特定屬性或特定屬性值或腳本值評估為時 `true` 。</span><span class="sxs-lookup"><span data-stu-id="c91f5-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="c91f5-132">如需選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c91f5-132">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="c91f5-133">如需更多有關廣泛視圖的元件的詳細資訊，請參閱 [建立廣泛的觀點](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="c91f5-133">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c91f5-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c91f5-134">See Also</span></span>

[<span data-ttu-id="c91f5-135">WideEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="c91f5-135">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="c91f5-136">適用于之 entryselectedby 的 WideEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="c91f5-136">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="c91f5-137">適用于之 entryselectedby 的 WideEntry (格式的 SelectionSetName 元素) </span><span class="sxs-lookup"><span data-stu-id="c91f5-137">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="c91f5-138">WideEntry 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c91f5-138">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="c91f5-139">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="c91f5-139">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="c91f5-140">定義用於顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="c91f5-140">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c91f5-141">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="c91f5-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
