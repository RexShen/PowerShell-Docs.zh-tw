---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 SelectionCondition 的 PropertyName 元素 (格式)
description: 設定之控制項的 SelectionCondition 的 PropertyName 元素 (格式)
ms.openlocfilehash: 5e4368a9546307c5ff223ae42ecaa1d2872bc587
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665952"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="61d8d-103">設定之控制項的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="61d8d-103">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="61d8d-104">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="61d8d-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="61d8d-105">當這個屬性存在或評估為時， `true` 就會符合條件，並且會使用此專案。</span><span class="sxs-lookup"><span data-stu-id="61d8d-105">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="61d8d-106">當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="61d8d-106">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="61d8d-107">設定元素 (格式) 控制項的設定元素 (格式) 控制項的設定 (格式) CustomEntries 專案 CustomControl 的設定 (格式) CustomEntry 專案的適用于設定 (格式的控制項的 CustomControl 格式) 之 entryselectedby 專案 CustomEntry 的設定 (格式) 之 entryselectedby for CustomEntry for SelectionCondition 的 SelectionCondition 專案 (格式) 的之 entryselectedby for ListEntry 的 (屬性) </span><span class="sxs-lookup"><span data-stu-id="61d8d-107">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="61d8d-108">語法</span><span class="sxs-lookup"><span data-stu-id="61d8d-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="61d8d-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="61d8d-109">Attributes and Elements</span></span>

<span data-ttu-id="61d8d-110">下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="61d8d-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="61d8d-111">屬性</span><span class="sxs-lookup"><span data-stu-id="61d8d-111">Attributes</span></span>

<span data-ttu-id="61d8d-112">無。</span><span class="sxs-lookup"><span data-stu-id="61d8d-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="61d8d-113">子元素</span><span class="sxs-lookup"><span data-stu-id="61d8d-113">Child Elements</span></span>

<span data-ttu-id="61d8d-114">無。</span><span class="sxs-lookup"><span data-stu-id="61d8d-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="61d8d-115">父項目</span><span class="sxs-lookup"><span data-stu-id="61d8d-115">Parent Elements</span></span>

|<span data-ttu-id="61d8d-116">元素</span><span class="sxs-lookup"><span data-stu-id="61d8d-116">Element</span></span>|<span data-ttu-id="61d8d-117">描述</span><span class="sxs-lookup"><span data-stu-id="61d8d-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="61d8d-118">設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="61d8d-118">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="61d8d-119">定義必須存在才能使用通用控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="61d8d-119">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="61d8d-120">文字值</span><span class="sxs-lookup"><span data-stu-id="61d8d-120">Text Value</span></span>

<span data-ttu-id="61d8d-121">指定 .NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="61d8d-121">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="61d8d-122">備註</span><span class="sxs-lookup"><span data-stu-id="61d8d-122">Remarks</span></span>

<span data-ttu-id="61d8d-123">選取條件必須指定至少一個屬性名稱或腳本，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="61d8d-123">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="61d8d-124">如需如何使用選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="61d8d-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="61d8d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61d8d-125">See Also</span></span>

[<span data-ttu-id="61d8d-126">設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="61d8d-126">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="61d8d-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="61d8d-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
