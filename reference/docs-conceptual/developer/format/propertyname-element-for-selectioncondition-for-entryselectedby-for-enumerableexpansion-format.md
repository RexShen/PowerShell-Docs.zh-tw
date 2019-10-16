---
title: EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ae11924-0072-451e-bf70-c5ffb25dccc0
caps.latest.revision: 13
ms.openlocfilehash: 0c20512e660c8d2b61d063dbd7078b55b23efeb8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362317"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="1ad97-102">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1ad97-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="1ad97-103">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="1ad97-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="1ad97-104">當這個屬性存在或評估為 `true` 時，就會符合條件，並使用定義。</span><span class="sxs-lookup"><span data-stu-id="1ad97-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="1ad97-105">EnumerableExpansion 的 SelectionCondition （Format）之 entryselectedby 元素的 DefaultSettings 元素（格式） EnumerableExpansions 元素（格式） EnumerableExpansion 元素（格式）之 entryselectedby 元素EnumerableExpansion 的之 entryselectedby 之 SelectionCondition 的 EnumerableExpansion （格式） PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1ad97-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1ad97-106">語法</span><span class="sxs-lookup"><span data-stu-id="1ad97-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1ad97-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="1ad97-107">Attributes and Elements</span></span>

<span data-ttu-id="1ad97-108">下列各節說明屬性、子專案，以及 `PropertyName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="1ad97-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1ad97-109">屬性</span><span class="sxs-lookup"><span data-stu-id="1ad97-109">Attributes</span></span>

<span data-ttu-id="1ad97-110">無。</span><span class="sxs-lookup"><span data-stu-id="1ad97-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1ad97-111">子元素</span><span class="sxs-lookup"><span data-stu-id="1ad97-111">Child Elements</span></span>

<span data-ttu-id="1ad97-112">無。</span><span class="sxs-lookup"><span data-stu-id="1ad97-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1ad97-113">父元素</span><span class="sxs-lookup"><span data-stu-id="1ad97-113">Parent Elements</span></span>

|<span data-ttu-id="1ad97-114">元素</span><span class="sxs-lookup"><span data-stu-id="1ad97-114">Element</span></span>|<span data-ttu-id="1ad97-115">描述</span><span class="sxs-lookup"><span data-stu-id="1ad97-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1ad97-116">EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1ad97-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="1ad97-117">定義必須存在的條件，才能展開這個定義的集合物件。</span><span class="sxs-lookup"><span data-stu-id="1ad97-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1ad97-118">文字值</span><span class="sxs-lookup"><span data-stu-id="1ad97-118">Text Value</span></span>

<span data-ttu-id="1ad97-119">指定 .NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="1ad97-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ad97-120">備註</span><span class="sxs-lookup"><span data-stu-id="1ad97-120">Remarks</span></span>

<span data-ttu-id="1ad97-121">選取條件必須指定至少一個屬性名稱或要評估的腳本，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="1ad97-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="1ad97-122">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="1ad97-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1ad97-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ad97-123">See Also</span></span>

[<span data-ttu-id="1ad97-124">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="1ad97-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1ad97-125">EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1ad97-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="1ad97-126">EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1ad97-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="1ad97-127">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="1ad97-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
