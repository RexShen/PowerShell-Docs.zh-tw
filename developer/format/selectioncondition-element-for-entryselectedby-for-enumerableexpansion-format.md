---
title: EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858284"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="e307d-102">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e307d-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="e307d-103">定義必須存在以展開此定義的集合物件的條件。</span><span class="sxs-lookup"><span data-stu-id="e307d-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="e307d-104">組態項目 （格式） DefaultSettings 項目 （格式） EnumerableExpansions 項目 （格式） EnumerableExpansion 項目 （格式） EntrySelectedBy 項目為 EntrySelectedBy EnumerableExpansion （格式） SelectionCondition 項目EnumerableExpansion （格式）</span><span class="sxs-lookup"><span data-stu-id="e307d-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e307d-105">語法</span><span class="sxs-lookup"><span data-stu-id="e307d-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e307d-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="e307d-106">Attributes and Elements</span></span>

<span data-ttu-id="e307d-107">下列各節說明屬性、 子項目和父項目`SelectionCondition`項目。</span><span class="sxs-lookup"><span data-stu-id="e307d-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="e307d-108">您必須指定單一`PropertyName`或`ScriptBlock`項目。</span><span class="sxs-lookup"><span data-stu-id="e307d-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="e307d-109">`SelectionSetName`和`TypeName`元素是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="e307d-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="e307d-110">您可以指定其中一個可能是項目。</span><span class="sxs-lookup"><span data-stu-id="e307d-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e307d-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e307d-111">Attributes</span></span>

<span data-ttu-id="e307d-112">無。</span><span class="sxs-lookup"><span data-stu-id="e307d-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e307d-113">子元素</span><span class="sxs-lookup"><span data-stu-id="e307d-113">Child Elements</span></span>

|<span data-ttu-id="e307d-114">元素</span><span class="sxs-lookup"><span data-stu-id="e307d-114">Element</span></span>|<span data-ttu-id="e307d-115">描述</span><span class="sxs-lookup"><span data-stu-id="e307d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e307d-116">PropertyName EnumerableExpansion （格式） 的 EntrySelectedBy 的 SelectionCondition 的項目</span><span class="sxs-lookup"><span data-stu-id="e307d-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="e307d-117">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="e307d-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e307d-118">指定觸發條件的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="e307d-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="e307d-119">針對 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="e307d-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="e307d-120">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="e307d-120">Optional element.</span></span><br /><br /> <span data-ttu-id="e307d-121">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="e307d-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="e307d-122">針對 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="e307d-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="e307d-123">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="e307d-123">Optional element.</span></span><br /><br /> <span data-ttu-id="e307d-124">指定觸發條件的.NET 型別集。</span><span class="sxs-lookup"><span data-stu-id="e307d-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="e307d-125">針對 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition TypeName 項目</span><span class="sxs-lookup"><span data-stu-id="e307d-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="e307d-126">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="e307d-126">Optional element.</span></span><br /><br /> <span data-ttu-id="e307d-127">指定觸發條件的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="e307d-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e307d-128">父元素</span><span class="sxs-lookup"><span data-stu-id="e307d-128">Parent Elements</span></span>

|<span data-ttu-id="e307d-129">元素</span><span class="sxs-lookup"><span data-stu-id="e307d-129">Element</span></span>|<span data-ttu-id="e307d-130">描述</span><span class="sxs-lookup"><span data-stu-id="e307d-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e307d-131">EntrySelectedBy EnumerableExpansion （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="e307d-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="e307d-132">定義此定義會展開.NET 集合物件。</span><span class="sxs-lookup"><span data-stu-id="e307d-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e307d-133">備註</span><span class="sxs-lookup"><span data-stu-id="e307d-133">Remarks</span></span>

<span data-ttu-id="e307d-134">每個定義必須至少一個型別名稱、 選取項目集或選擇條件的定義。</span><span class="sxs-lookup"><span data-stu-id="e307d-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="e307d-135">在您定義的選取範圍條件時，適用下列需求：</span><span class="sxs-lookup"><span data-stu-id="e307d-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="e307d-136">選取條件必須指定至少一個屬性名稱或指令碼區塊，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="e307d-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="e307d-137">選取條件可以指定任意數目的.NET 型別，或選取項目集，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="e307d-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="e307d-138">如需如何使用選擇條件的詳細資訊，請參閱[定義條件 Diplaying 資料](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e307d-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e307d-139">寬型檢視的其他元件的相關資訊，請參閱[寬型檢視](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="e307d-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e307d-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e307d-140">See Also</span></span>

[<span data-ttu-id="e307d-141">定義何時顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="e307d-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e307d-142">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="e307d-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
