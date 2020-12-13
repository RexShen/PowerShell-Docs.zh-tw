---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)
description: EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)
ms.openlocfilehash: bd72a9bc914ea6543d8dab768b5e20e9a580ada7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664896"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="85961-103">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="85961-103">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="85961-104">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="85961-104">Specifies the script that triggers the condition.</span></span>

<span data-ttu-id="85961-105">設定元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 元素 (格式) EnumerableExpansion 元素 (格式) 之 entryselectedby 專案 (格式) EnumerableExpansion 的 SelectionCondition (格式) 之 entryselectedby for EnumerableExpansion 的 SelectionCondition (格式) </span><span class="sxs-lookup"><span data-stu-id="85961-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="85961-106">語法</span><span class="sxs-lookup"><span data-stu-id="85961-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="85961-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="85961-107">Attributes and Elements</span></span>

<span data-ttu-id="85961-108">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="85961-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="85961-109">屬性</span><span class="sxs-lookup"><span data-stu-id="85961-109">Attributes</span></span>

<span data-ttu-id="85961-110">無。</span><span class="sxs-lookup"><span data-stu-id="85961-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="85961-111">子元素</span><span class="sxs-lookup"><span data-stu-id="85961-111">Child Elements</span></span>

<span data-ttu-id="85961-112">無。</span><span class="sxs-lookup"><span data-stu-id="85961-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="85961-113">父項目</span><span class="sxs-lookup"><span data-stu-id="85961-113">Parent Elements</span></span>

|<span data-ttu-id="85961-114">元素</span><span class="sxs-lookup"><span data-stu-id="85961-114">Element</span></span>|<span data-ttu-id="85961-115">描述</span><span class="sxs-lookup"><span data-stu-id="85961-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="85961-116">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="85961-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="85961-117">定義必須存在才能展開這個定義之集合物件的條件。</span><span class="sxs-lookup"><span data-stu-id="85961-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="85961-118">文字值</span><span class="sxs-lookup"><span data-stu-id="85961-118">Text Value</span></span>

<span data-ttu-id="85961-119">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="85961-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="85961-120">備註</span><span class="sxs-lookup"><span data-stu-id="85961-120">Remarks</span></span>

<span data-ttu-id="85961-121">選取條件必須指定至少一個要評估的腳本或屬性名稱，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="85961-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="85961-122">如需如何使用選取條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="85961-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="85961-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85961-123">See Also</span></span>

[<span data-ttu-id="85961-124">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="85961-124">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="85961-125">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="85961-125">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="85961-126">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="85961-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="85961-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="85961-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
