---
title: EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362007"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="89560-102">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="89560-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="89560-103">定義必須存在的條件，才能展開這個定義的集合物件。</span><span class="sxs-lookup"><span data-stu-id="89560-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="89560-104">EnumerableExpansion 的 SelectionCondition （Format）之 entryselectedby 元素的 DefaultSettings 元素（格式） EnumerableExpansions 元素（格式） EnumerableExpansion 元素（格式）之 entryselectedby 元素EnumerableExpansion （格式）</span><span class="sxs-lookup"><span data-stu-id="89560-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="89560-105">語法</span><span class="sxs-lookup"><span data-stu-id="89560-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="89560-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="89560-106">Attributes and Elements</span></span>

<span data-ttu-id="89560-107">下列各節說明屬性、子專案，以及 `SelectionCondition` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="89560-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="89560-108">您必須指定單一 `PropertyName` 或 @no__t 1 元素。</span><span class="sxs-lookup"><span data-stu-id="89560-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="89560-109">@No__t-0 和 @no__t 1 元素是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="89560-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="89560-110">您可以指定其中一個元素。</span><span class="sxs-lookup"><span data-stu-id="89560-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="89560-111">屬性</span><span class="sxs-lookup"><span data-stu-id="89560-111">Attributes</span></span>

<span data-ttu-id="89560-112">無。</span><span class="sxs-lookup"><span data-stu-id="89560-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="89560-113">子元素</span><span class="sxs-lookup"><span data-stu-id="89560-113">Child Elements</span></span>

|<span data-ttu-id="89560-114">元素</span><span class="sxs-lookup"><span data-stu-id="89560-114">Element</span></span>|<span data-ttu-id="89560-115">描述</span><span class="sxs-lookup"><span data-stu-id="89560-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="89560-116">EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="89560-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="89560-117">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="89560-117">Optional element.</span></span><br /><br /> <span data-ttu-id="89560-118">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="89560-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="89560-119">EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="89560-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="89560-120">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="89560-120">Optional element.</span></span><br /><br /> <span data-ttu-id="89560-121">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="89560-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="89560-122">EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="89560-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="89560-123">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="89560-123">Optional element.</span></span><br /><br /> <span data-ttu-id="89560-124">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="89560-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="89560-125">EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="89560-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="89560-126">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="89560-126">Optional element.</span></span><br /><br /> <span data-ttu-id="89560-127">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="89560-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="89560-128">父元素</span><span class="sxs-lookup"><span data-stu-id="89560-128">Parent Elements</span></span>

|<span data-ttu-id="89560-129">元素</span><span class="sxs-lookup"><span data-stu-id="89560-129">Element</span></span>|<span data-ttu-id="89560-130">描述</span><span class="sxs-lookup"><span data-stu-id="89560-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="89560-131">EnumerableExpansion 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="89560-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="89560-132">定義由這個定義擴充的 .NET 集合物件。</span><span class="sxs-lookup"><span data-stu-id="89560-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="89560-133">備註</span><span class="sxs-lookup"><span data-stu-id="89560-133">Remarks</span></span>

<span data-ttu-id="89560-134">每個定義都必須定義至少一個型別名稱、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="89560-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="89560-135">當您定義選取條件時，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="89560-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="89560-136">選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="89560-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="89560-137">選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="89560-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="89560-138">如需如何使用選取條件的詳細資訊，請參閱[定義 Diplaying 資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="89560-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="89560-139">如需有關寬視圖之其他元件的詳細資訊，請參閱[Wide view](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="89560-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="89560-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89560-140">See Also</span></span>

[<span data-ttu-id="89560-141">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="89560-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="89560-142">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="89560-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)