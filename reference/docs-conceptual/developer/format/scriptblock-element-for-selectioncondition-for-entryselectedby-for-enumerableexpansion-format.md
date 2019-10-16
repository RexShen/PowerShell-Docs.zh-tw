---
title: EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368607"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="93776-102">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="93776-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="93776-103">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="93776-103">Specifies the script that triggers the condition.</span></span>

<span data-ttu-id="93776-104">EnumerableExpansion 的 SelectionCondition （Format）之 entryselectedby 元素的 DefaultSettings 元素（格式） EnumerableExpansions 元素（格式） EnumerableExpansion 元素（格式）之 entryselectedby 元素EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 EnumerableExpansion （格式） ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="93776-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="93776-105">語法</span><span class="sxs-lookup"><span data-stu-id="93776-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="93776-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="93776-106">Attributes and Elements</span></span>

<span data-ttu-id="93776-107">下列各節說明屬性、子專案，以及 `ScriptBlock` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="93776-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="93776-108">屬性</span><span class="sxs-lookup"><span data-stu-id="93776-108">Attributes</span></span>

<span data-ttu-id="93776-109">無。</span><span class="sxs-lookup"><span data-stu-id="93776-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="93776-110">子元素</span><span class="sxs-lookup"><span data-stu-id="93776-110">Child Elements</span></span>

<span data-ttu-id="93776-111">無。</span><span class="sxs-lookup"><span data-stu-id="93776-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="93776-112">父元素</span><span class="sxs-lookup"><span data-stu-id="93776-112">Parent Elements</span></span>

|<span data-ttu-id="93776-113">元素</span><span class="sxs-lookup"><span data-stu-id="93776-113">Element</span></span>|<span data-ttu-id="93776-114">描述</span><span class="sxs-lookup"><span data-stu-id="93776-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="93776-115">EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="93776-115">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="93776-116">定義必須存在的條件，才能展開這個定義的集合物件。</span><span class="sxs-lookup"><span data-stu-id="93776-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="93776-117">文字值</span><span class="sxs-lookup"><span data-stu-id="93776-117">Text Value</span></span>

<span data-ttu-id="93776-118">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="93776-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="93776-119">備註</span><span class="sxs-lookup"><span data-stu-id="93776-119">Remarks</span></span>

<span data-ttu-id="93776-120">選取條件必須指定至少一個要評估的腳本或屬性名稱，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="93776-120">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="93776-121">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="93776-121">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="93776-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93776-122">See Also</span></span>

[<span data-ttu-id="93776-123">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="93776-123">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="93776-124">EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="93776-124">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="93776-125">EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="93776-125">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="93776-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="93776-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
