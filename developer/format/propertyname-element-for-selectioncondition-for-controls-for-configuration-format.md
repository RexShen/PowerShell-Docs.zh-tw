---
title: PropertyName SelectionCondition 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861024"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="7166c-102">設定之控制項的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7166c-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="7166c-103">指定觸發條件的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="7166c-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="7166c-104">當這個屬性是存在，或當其評估結果為`true`、 符合條件，和使用的項目。</span><span class="sxs-lookup"><span data-stu-id="7166c-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="7166c-105">定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="7166c-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="7166c-106">組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目CustomControl CustomEntry 的組態 （格式） 的組態 （如 CustomEntry EntrySelectedBy 的 SelectionCondition 項目控制項的組態 （格式） EntrySelectedBy 元素的控制項的格式） CustomEntry 項目針對 ListEntry （格式） 的 EntrySelectedBy SelectionCondition 的格式） PropertyName 項目</span><span class="sxs-lookup"><span data-stu-id="7166c-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7166c-107">語法</span><span class="sxs-lookup"><span data-stu-id="7166c-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7166c-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="7166c-108">Attributes and Elements</span></span>

<span data-ttu-id="7166c-109">下列各節說明屬性、 子項目和父項目`PropertyName`項目。</span><span class="sxs-lookup"><span data-stu-id="7166c-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7166c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="7166c-110">Attributes</span></span>

<span data-ttu-id="7166c-111">無。</span><span class="sxs-lookup"><span data-stu-id="7166c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7166c-112">子元素</span><span class="sxs-lookup"><span data-stu-id="7166c-112">Child Elements</span></span>

<span data-ttu-id="7166c-113">無。</span><span class="sxs-lookup"><span data-stu-id="7166c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7166c-114">父元素</span><span class="sxs-lookup"><span data-stu-id="7166c-114">Parent Elements</span></span>

|<span data-ttu-id="7166c-115">元素</span><span class="sxs-lookup"><span data-stu-id="7166c-115">Element</span></span>|<span data-ttu-id="7166c-116">描述</span><span class="sxs-lookup"><span data-stu-id="7166c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7166c-117">SelectionCondition EntrySelectedBy 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="7166c-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="7166c-118">定義必須存在，要使用的通用控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="7166c-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7166c-119">文字值</span><span class="sxs-lookup"><span data-stu-id="7166c-119">Text Value</span></span>

<span data-ttu-id="7166c-120">指定.NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="7166c-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="7166c-121">備註</span><span class="sxs-lookup"><span data-stu-id="7166c-121">Remarks</span></span>

<span data-ttu-id="7166c-122">選取條件必須指定至少一個屬性名稱或指令碼，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="7166c-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="7166c-123">如需如何使用選擇條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7166c-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7166c-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7166c-124">See Also</span></span>

[<span data-ttu-id="7166c-125">SelectionCondition EntrySelectedBy 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="7166c-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="7166c-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="7166c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
