---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)
description: EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)
ms.openlocfilehash: 8e28118894661b50e90a5ccc86a36fbbe77e4b03
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665833"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="e2a2f-103">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e2a2f-103">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="e2a2f-104">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="e2a2f-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="e2a2f-105">當這個屬性存在或評估為時， `true` 就會符合條件，並使用定義。</span><span class="sxs-lookup"><span data-stu-id="e2a2f-105">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="e2a2f-106">設定元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 專案 (格式) EnumerableExpansion 元素 (格式) 之 entryselectedby 專案 (格式) EnumerableExpansion 的 SelectionCondition 專案 (格式) 之 entryselectedby for EnumerableExpansion 的 SelectionCondition (格式) </span><span class="sxs-lookup"><span data-stu-id="e2a2f-106">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e2a2f-107">語法</span><span class="sxs-lookup"><span data-stu-id="e2a2f-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e2a2f-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e2a2f-108">Attributes and Elements</span></span>

<span data-ttu-id="e2a2f-109">下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="e2a2f-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e2a2f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e2a2f-110">Attributes</span></span>

<span data-ttu-id="e2a2f-111">無。</span><span class="sxs-lookup"><span data-stu-id="e2a2f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e2a2f-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e2a2f-112">Child Elements</span></span>

<span data-ttu-id="e2a2f-113">無。</span><span class="sxs-lookup"><span data-stu-id="e2a2f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e2a2f-114">父項目</span><span class="sxs-lookup"><span data-stu-id="e2a2f-114">Parent Elements</span></span>

|<span data-ttu-id="e2a2f-115">元素</span><span class="sxs-lookup"><span data-stu-id="e2a2f-115">Element</span></span>|<span data-ttu-id="e2a2f-116">描述</span><span class="sxs-lookup"><span data-stu-id="e2a2f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e2a2f-117">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e2a2f-117">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="e2a2f-118">定義必須存在才能展開這個定義之集合物件的條件。</span><span class="sxs-lookup"><span data-stu-id="e2a2f-118">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e2a2f-119">文字值</span><span class="sxs-lookup"><span data-stu-id="e2a2f-119">Text Value</span></span>

<span data-ttu-id="e2a2f-120">指定 .NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="e2a2f-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="e2a2f-121">備註</span><span class="sxs-lookup"><span data-stu-id="e2a2f-121">Remarks</span></span>

<span data-ttu-id="e2a2f-122">選取條件必須指定至少一個屬性名稱或要評估的腳本，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="e2a2f-122">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="e2a2f-123">如需如何使用選取條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e2a2f-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2a2f-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2a2f-124">See Also</span></span>

[<span data-ttu-id="e2a2f-125">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="e2a2f-125">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e2a2f-126">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e2a2f-126">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="e2a2f-127">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e2a2f-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="e2a2f-128">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="e2a2f-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
