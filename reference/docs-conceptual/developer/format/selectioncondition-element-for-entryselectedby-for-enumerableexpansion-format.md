---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)
description: EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)
ms.openlocfilehash: 3ecf7fde99b9ee66a153eea416792f351ff62af3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647919"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="2f03f-103">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2f03f-103">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="2f03f-104">定義必須存在才能展開這個定義之集合物件的條件。</span><span class="sxs-lookup"><span data-stu-id="2f03f-104">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="2f03f-105">設定元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 專案 (格式) EnumerableExpansion 元素 (格式) 之 entryselectedby 專案的 EnumerableExpansion (格式) SelectionCondition 專案之 entryselectedby 的 EnumerableExpansion (格式) </span><span class="sxs-lookup"><span data-stu-id="2f03f-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2f03f-106">語法</span><span class="sxs-lookup"><span data-stu-id="2f03f-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2f03f-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2f03f-107">Attributes and Elements</span></span>

<span data-ttu-id="2f03f-108">下列各節說明屬性、子專案和元素的父元素 `SelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="2f03f-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="2f03f-109">您必須指定單一 `PropertyName` 或 `ScriptBlock` 元素。</span><span class="sxs-lookup"><span data-stu-id="2f03f-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="2f03f-110">`SelectionSetName`和 `TypeName` 元素是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="2f03f-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="2f03f-111">您可以指定其中一個元素。</span><span class="sxs-lookup"><span data-stu-id="2f03f-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2f03f-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2f03f-112">Attributes</span></span>

<span data-ttu-id="2f03f-113">無。</span><span class="sxs-lookup"><span data-stu-id="2f03f-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2f03f-114">子元素</span><span class="sxs-lookup"><span data-stu-id="2f03f-114">Child Elements</span></span>

|<span data-ttu-id="2f03f-115">元素</span><span class="sxs-lookup"><span data-stu-id="2f03f-115">Element</span></span>|<span data-ttu-id="2f03f-116">描述</span><span class="sxs-lookup"><span data-stu-id="2f03f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2f03f-117">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2f03f-117">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="2f03f-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="2f03f-118">Optional element.</span></span><br /><br /> <span data-ttu-id="2f03f-119">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="2f03f-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="2f03f-120">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2f03f-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="2f03f-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="2f03f-121">Optional element.</span></span><br /><br /> <span data-ttu-id="2f03f-122">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="2f03f-122">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="2f03f-123">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2f03f-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="2f03f-124">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="2f03f-124">Optional element.</span></span><br /><br /> <span data-ttu-id="2f03f-125">指定一組觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="2f03f-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="2f03f-126">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2f03f-126">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="2f03f-127">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="2f03f-127">Optional element.</span></span><br /><br /> <span data-ttu-id="2f03f-128">指定觸發條件的 .NET 型別。</span><span class="sxs-lookup"><span data-stu-id="2f03f-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2f03f-129">父項目</span><span class="sxs-lookup"><span data-stu-id="2f03f-129">Parent Elements</span></span>

|<span data-ttu-id="2f03f-130">元素</span><span class="sxs-lookup"><span data-stu-id="2f03f-130">Element</span></span>|<span data-ttu-id="2f03f-131">描述</span><span class="sxs-lookup"><span data-stu-id="2f03f-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2f03f-132">EnumerableExpansion 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2f03f-132">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="2f03f-133">定義由這個定義擴充的 .NET 集合物件。</span><span class="sxs-lookup"><span data-stu-id="2f03f-133">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2f03f-134">備註</span><span class="sxs-lookup"><span data-stu-id="2f03f-134">Remarks</span></span>

<span data-ttu-id="2f03f-135">每個定義都必須定義至少一個型別名稱、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="2f03f-135">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="2f03f-136">當您定義選取條件時，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="2f03f-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="2f03f-137">選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="2f03f-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="2f03f-138">選取條件可以指定任意數目的 .NET 類型或選取集，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="2f03f-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="2f03f-139">如需如何使用選取條件的詳細資訊，請參閱 [定義 Diplaying 資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="2f03f-139">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="2f03f-140">如需廣泛視圖的其他元件的詳細資訊，請參閱 [Wide view](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="2f03f-140">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2f03f-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f03f-141">See Also</span></span>

[<span data-ttu-id="2f03f-142">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="2f03f-142">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2f03f-143">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="2f03f-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
