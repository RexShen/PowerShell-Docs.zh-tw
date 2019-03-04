---
title: PropertyName WideEntry （格式） 的 EntrySelectedBy 的 SelectionCondition 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860414"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="7bd67-102">WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7bd67-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="7bd67-103">指定觸發條件的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="7bd67-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="7bd67-104">當這個屬性是存在，或當其評估結果為`true`、 符合條件，和在使用定義。</span><span class="sxs-lookup"><span data-stu-id="7bd67-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="7bd67-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry 項目 （格式） EntrySelectedBy 項目用於 WideEntry （格式） SelectionCondition 元素EntrySelectedBy WideEntry （格式） 的 EntrySelectedBy 的 SelectionCondition WideEntry （格式） PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="7bd67-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7bd67-106">語法</span><span class="sxs-lookup"><span data-stu-id="7bd67-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="7bd67-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="7bd67-107">Attributes and Elements</span></span>

<span data-ttu-id="7bd67-108">下列各節說明屬性、 子項目和父項目`PropertyName`項目。</span><span class="sxs-lookup"><span data-stu-id="7bd67-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7bd67-109">屬性</span><span class="sxs-lookup"><span data-stu-id="7bd67-109">Attributes</span></span>

<span data-ttu-id="7bd67-110">無。</span><span class="sxs-lookup"><span data-stu-id="7bd67-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7bd67-111">子元素</span><span class="sxs-lookup"><span data-stu-id="7bd67-111">Child Elements</span></span>

<span data-ttu-id="7bd67-112">無。</span><span class="sxs-lookup"><span data-stu-id="7bd67-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7bd67-113">父元素</span><span class="sxs-lookup"><span data-stu-id="7bd67-113">Parent Elements</span></span>

|<span data-ttu-id="7bd67-114">元素</span><span class="sxs-lookup"><span data-stu-id="7bd67-114">Element</span></span>|<span data-ttu-id="7bd67-115">描述</span><span class="sxs-lookup"><span data-stu-id="7bd67-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7bd67-116">WideEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="7bd67-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="7bd67-117">定義要使用此定義必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="7bd67-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7bd67-118">文字值</span><span class="sxs-lookup"><span data-stu-id="7bd67-118">Text Value</span></span>

<span data-ttu-id="7bd67-119">指定.NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="7bd67-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="7bd67-120">備註</span><span class="sxs-lookup"><span data-stu-id="7bd67-120">Remarks</span></span>

<span data-ttu-id="7bd67-121">選取條件必須指定至少一個屬性名稱或指令碼，以評估，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="7bd67-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="7bd67-122">如需如何使用選擇條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7bd67-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="7bd67-123">寬型檢視的其他元件的相關資訊，請參閱[寬型檢視](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="7bd67-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7bd67-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bd67-124">See Also</span></span>

[<span data-ttu-id="7bd67-125">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="7bd67-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="7bd67-126">定義何時顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="7bd67-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7bd67-127">針對 WideEntry （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="7bd67-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="7bd67-128">WideEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="7bd67-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="7bd67-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="7bd67-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
