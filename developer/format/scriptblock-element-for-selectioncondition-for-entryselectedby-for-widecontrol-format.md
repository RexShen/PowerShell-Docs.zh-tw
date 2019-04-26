---
title: 針對 WideControl （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064317"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="69558-102">WideControl 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="69558-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="69558-103">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="69558-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="69558-104">此指令碼會評估為`true`、 符合條件，和使用寬的項目定義。</span><span class="sxs-lookup"><span data-stu-id="69558-104">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="69558-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry 項目 （格式） EntrySelectedBy 項目用於 WideEntry （格式） SelectionCondition 元素EntrySelectedBy WideEntry （格式） 的 EntrySelectedBy 的 SelectionCondition WideEntry （格式） ScriptBlock 元素</span><span class="sxs-lookup"><span data-stu-id="69558-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="69558-106">語法</span><span class="sxs-lookup"><span data-stu-id="69558-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="69558-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="69558-107">Attributes and Elements</span></span>

<span data-ttu-id="69558-108">下列各節說明屬性、 子項目和父項目`ScriptBlock`項目。</span><span class="sxs-lookup"><span data-stu-id="69558-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="69558-109">屬性</span><span class="sxs-lookup"><span data-stu-id="69558-109">Attributes</span></span>

<span data-ttu-id="69558-110">無。</span><span class="sxs-lookup"><span data-stu-id="69558-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="69558-111">子元素</span><span class="sxs-lookup"><span data-stu-id="69558-111">Child Elements</span></span>

<span data-ttu-id="69558-112">無。</span><span class="sxs-lookup"><span data-stu-id="69558-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="69558-113">父項目</span><span class="sxs-lookup"><span data-stu-id="69558-113">Parent Elements</span></span>

|<span data-ttu-id="69558-114">項目</span><span class="sxs-lookup"><span data-stu-id="69558-114">Element</span></span>|<span data-ttu-id="69558-115">描述</span><span class="sxs-lookup"><span data-stu-id="69558-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="69558-116">WideEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="69558-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="69558-117">定義要使用此定義必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="69558-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="69558-118">文字值</span><span class="sxs-lookup"><span data-stu-id="69558-118">Text Value</span></span>

<span data-ttu-id="69558-119">指定評估指令碼。</span><span class="sxs-lookup"><span data-stu-id="69558-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="69558-120">備註</span><span class="sxs-lookup"><span data-stu-id="69558-120">Remarks</span></span>

<span data-ttu-id="69558-121">選取條件必須指定至少一個指令碼或屬性名稱，若要評估，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="69558-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="69558-122">如需如何使用選擇條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="69558-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="69558-123">寬型檢視的其他元件的相關資訊，請參閱[寬型檢視](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="69558-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="69558-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69558-124">See Also</span></span>

[<span data-ttu-id="69558-125">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="69558-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="69558-126">定義何時顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="69558-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="69558-127">PropertyName WideEntry （格式） 的 EntrySelectedBy 的 SelectionCondition 的項目</span><span class="sxs-lookup"><span data-stu-id="69558-127">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="69558-128">WideEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="69558-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="69558-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="69558-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
