---
title: PropertyName EnumerableExpansion （格式） 的 EntrySelectedBy 的 SelectionCondition 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ae11924-0072-451e-bf70-c5ffb25dccc0
caps.latest.revision: 13
ms.openlocfilehash: 0c20512e660c8d2b61d063dbd7078b55b23efeb8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859624"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="bd778-102">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bd778-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="bd778-103">指定觸發條件的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="bd778-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="bd778-104">當這個屬性是存在，或當其評估結果為`true`、 符合條件，和在使用定義。</span><span class="sxs-lookup"><span data-stu-id="bd778-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="bd778-105">組態項目 （格式） DefaultSettings 項目 （格式） EnumerableExpansions 項目 （格式） EnumerableExpansion 項目 （格式） EntrySelectedBy 項目為 EntrySelectedBy EnumerableExpansion （格式） SelectionCondition 項目針對 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition EnumerableExpansion （格式） PropertyName 項目</span><span class="sxs-lookup"><span data-stu-id="bd778-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bd778-106">語法</span><span class="sxs-lookup"><span data-stu-id="bd778-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bd778-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="bd778-107">Attributes and Elements</span></span>

<span data-ttu-id="bd778-108">下列各節說明屬性、 子項目和父項目`PropertyName`項目。</span><span class="sxs-lookup"><span data-stu-id="bd778-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bd778-109">屬性</span><span class="sxs-lookup"><span data-stu-id="bd778-109">Attributes</span></span>

<span data-ttu-id="bd778-110">無。</span><span class="sxs-lookup"><span data-stu-id="bd778-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bd778-111">子元素</span><span class="sxs-lookup"><span data-stu-id="bd778-111">Child Elements</span></span>

<span data-ttu-id="bd778-112">無。</span><span class="sxs-lookup"><span data-stu-id="bd778-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bd778-113">父元素</span><span class="sxs-lookup"><span data-stu-id="bd778-113">Parent Elements</span></span>

|<span data-ttu-id="bd778-114">元素</span><span class="sxs-lookup"><span data-stu-id="bd778-114">Element</span></span>|<span data-ttu-id="bd778-115">描述</span><span class="sxs-lookup"><span data-stu-id="bd778-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bd778-116">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="bd778-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="bd778-117">定義必須存在以展開此定義的集合物件的條件。</span><span class="sxs-lookup"><span data-stu-id="bd778-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bd778-118">文字值</span><span class="sxs-lookup"><span data-stu-id="bd778-118">Text Value</span></span>

<span data-ttu-id="bd778-119">指定.NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="bd778-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="bd778-120">備註</span><span class="sxs-lookup"><span data-stu-id="bd778-120">Remarks</span></span>

<span data-ttu-id="bd778-121">選取條件必須指定至少一個屬性名稱或指令碼，以評估，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="bd778-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="bd778-122">如需如何使用選擇條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="bd778-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bd778-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd778-123">See Also</span></span>

[<span data-ttu-id="bd778-124">定義條件的資料時顯示</span><span class="sxs-lookup"><span data-stu-id="bd778-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="bd778-125">針對 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="bd778-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="bd778-126">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="bd778-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="bd778-127">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="bd778-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
