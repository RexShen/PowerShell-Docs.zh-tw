---
title: PropertyName SelectionCondition 如 CustomControl 檢視 （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48a417-2083-46d4-ac38-16c12e65b6b9
caps.latest.revision: 7
ms.openlocfilehash: e08037d5d051d3be51e90193c7e87cc2e738f78a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064691"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="ee831-102">檢視之 CustomControl 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ee831-102">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="ee831-103">指定觸發條件的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="ee831-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="ee831-104">當這個屬性是存在，或當其評估結果為`true`、 符合條件，和在使用定義。</span><span class="sxs-lookup"><span data-stu-id="ee831-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="ee831-105">定義自訂控制項的檢視時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="ee831-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="ee831-106">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目進行檢視 （格式） 的檢視 （如 CustomControl CustomEntries CustomEntry 元素 CustomControl 的檢視 （格式） CustomEntries 項目格式） 的檢視 （格式） 的檢視 （格式） 的檢視 （格式） m CustomControl EntrySelectedBy SelectionCondition 元素 CustomControl CustomEntry EntrySelectedBy 元素 CustomControl CustomEntry CustomItem 項目SelectionCondition CustomControl 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="ee831-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ee831-107">語法</span><span class="sxs-lookup"><span data-stu-id="ee831-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ee831-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ee831-108">Attributes and Elements</span></span>

<span data-ttu-id="ee831-109">下列各節說明屬性、 子項目和父項目`PropertyName`項目。</span><span class="sxs-lookup"><span data-stu-id="ee831-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ee831-110">屬性</span><span class="sxs-lookup"><span data-stu-id="ee831-110">Attributes</span></span>

<span data-ttu-id="ee831-111">無。</span><span class="sxs-lookup"><span data-stu-id="ee831-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ee831-112">子元素</span><span class="sxs-lookup"><span data-stu-id="ee831-112">Child Elements</span></span>

<span data-ttu-id="ee831-113">無。</span><span class="sxs-lookup"><span data-stu-id="ee831-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ee831-114">父項目</span><span class="sxs-lookup"><span data-stu-id="ee831-114">Parent Elements</span></span>

|<span data-ttu-id="ee831-115">項目</span><span class="sxs-lookup"><span data-stu-id="ee831-115">Element</span></span>|<span data-ttu-id="ee831-116">描述</span><span class="sxs-lookup"><span data-stu-id="ee831-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ee831-117">CustomControl 檢視 （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="ee831-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="ee831-118">定義必須存在，要使用的控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="ee831-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ee831-119">文字值</span><span class="sxs-lookup"><span data-stu-id="ee831-119">Text Value</span></span>

<span data-ttu-id="ee831-120">指定.NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="ee831-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="ee831-121">備註</span><span class="sxs-lookup"><span data-stu-id="ee831-121">Remarks</span></span>

<span data-ttu-id="ee831-122">選取條件必須指定至少一個屬性名稱或指令碼，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="ee831-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="ee831-123">如需如何使用選擇條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="ee831-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ee831-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee831-124">See Also</span></span>

[<span data-ttu-id="ee831-125">CustomControl 檢視 （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="ee831-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="ee831-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="ee831-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
