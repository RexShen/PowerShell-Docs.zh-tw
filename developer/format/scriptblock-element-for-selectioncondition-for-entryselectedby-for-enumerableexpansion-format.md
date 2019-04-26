---
title: 針對 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064368"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="68a7b-102">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="68a7b-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="68a7b-103">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="68a7b-103">Specifies the script that triggers the condition.</span></span>

<span data-ttu-id="68a7b-104">組態項目 （格式） DefaultSettings 項目 （格式） EnumerableExpansions 項目 （格式） EnumerableExpansion 項目 （格式） EntrySelectedBy 項目為 EntrySelectedBy EnumerableExpansion （格式） SelectionCondition 項目針對 EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition EnumerableExpansion （格式） 指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="68a7b-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="68a7b-105">語法</span><span class="sxs-lookup"><span data-stu-id="68a7b-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="68a7b-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="68a7b-106">Attributes and Elements</span></span>

<span data-ttu-id="68a7b-107">下列各節說明屬性、 子項目和父項目`ScriptBlock`項目。</span><span class="sxs-lookup"><span data-stu-id="68a7b-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="68a7b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="68a7b-108">Attributes</span></span>

<span data-ttu-id="68a7b-109">無。</span><span class="sxs-lookup"><span data-stu-id="68a7b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="68a7b-110">子元素</span><span class="sxs-lookup"><span data-stu-id="68a7b-110">Child Elements</span></span>

<span data-ttu-id="68a7b-111">無。</span><span class="sxs-lookup"><span data-stu-id="68a7b-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="68a7b-112">父項目</span><span class="sxs-lookup"><span data-stu-id="68a7b-112">Parent Elements</span></span>

|<span data-ttu-id="68a7b-113">項目</span><span class="sxs-lookup"><span data-stu-id="68a7b-113">Element</span></span>|<span data-ttu-id="68a7b-114">描述</span><span class="sxs-lookup"><span data-stu-id="68a7b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="68a7b-115">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="68a7b-115">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="68a7b-116">定義必須存在以展開此定義的集合物件的條件。</span><span class="sxs-lookup"><span data-stu-id="68a7b-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="68a7b-117">文字值</span><span class="sxs-lookup"><span data-stu-id="68a7b-117">Text Value</span></span>

<span data-ttu-id="68a7b-118">指定評估指令碼。</span><span class="sxs-lookup"><span data-stu-id="68a7b-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="68a7b-119">備註</span><span class="sxs-lookup"><span data-stu-id="68a7b-119">Remarks</span></span>

<span data-ttu-id="68a7b-120">選取條件必須指定至少一個指令碼或屬性名稱，若要評估，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="68a7b-120">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="68a7b-121">如需如何使用選擇條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="68a7b-121">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="68a7b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68a7b-122">See Also</span></span>

[<span data-ttu-id="68a7b-123">定義何時顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="68a7b-123">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="68a7b-124">PropertyName EnumerableExpansion （格式） 的 EntrySelectedBy 的 SelectionCondition 的項目</span><span class="sxs-lookup"><span data-stu-id="68a7b-124">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="68a7b-125">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="68a7b-125">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="68a7b-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="68a7b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
