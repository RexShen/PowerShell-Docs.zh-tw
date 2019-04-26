---
title: GroupBy （格式） 的 EntrySelectedBy 的 SelectionCondition 的指令碼區塊項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e01344bd-ad69-4789-8e9f-2e79880c3a33
caps.latest.revision: 6
ms.openlocfilehash: cb79fb942111cee89c6b2abba75de4c494082b7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064334"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="1911b-102">GroupBy 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1911b-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="1911b-103">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="1911b-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="1911b-104">此指令碼會評估為`true`、 符合條件，和在使用定義。</span><span class="sxs-lookup"><span data-stu-id="1911b-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="1911b-105">定義新的群組物件的顯示方式時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="1911b-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="1911b-106">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素CustomControl CustomEntry EntrySelectedBy SelectionCondition 的 GroupBy （格式） 的 GroupBy （格式） ScriptBlock 元素的 GroupBy （格式） SelectionCondition 元素的 GroupBy （格式） EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="1911b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1911b-107">語法</span><span class="sxs-lookup"><span data-stu-id="1911b-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1911b-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1911b-108">Attributes and Elements</span></span>

<span data-ttu-id="1911b-109">下列各節說明屬性、 子項目和父項目`ScriptBlock`項目。</span><span class="sxs-lookup"><span data-stu-id="1911b-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1911b-110">屬性</span><span class="sxs-lookup"><span data-stu-id="1911b-110">Attributes</span></span>

<span data-ttu-id="1911b-111">無。</span><span class="sxs-lookup"><span data-stu-id="1911b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1911b-112">子元素</span><span class="sxs-lookup"><span data-stu-id="1911b-112">Child Elements</span></span>

<span data-ttu-id="1911b-113">無。</span><span class="sxs-lookup"><span data-stu-id="1911b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1911b-114">父項目</span><span class="sxs-lookup"><span data-stu-id="1911b-114">Parent Elements</span></span>

|<span data-ttu-id="1911b-115">項目</span><span class="sxs-lookup"><span data-stu-id="1911b-115">Element</span></span>|<span data-ttu-id="1911b-116">描述</span><span class="sxs-lookup"><span data-stu-id="1911b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1911b-117">GroupBy （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="1911b-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="1911b-118">定義必須存在，要使用的控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="1911b-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1911b-119">文字值</span><span class="sxs-lookup"><span data-stu-id="1911b-119">Text Value</span></span>

<span data-ttu-id="1911b-120">指定評估指令碼。</span><span class="sxs-lookup"><span data-stu-id="1911b-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="1911b-121">備註</span><span class="sxs-lookup"><span data-stu-id="1911b-121">Remarks</span></span>

<span data-ttu-id="1911b-122">選取條件必須指定至少一個指令碼或屬性名稱來評估，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="1911b-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="1911b-123">如需如何使用選擇條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="1911b-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1911b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1911b-124">See Also</span></span>

[<span data-ttu-id="1911b-125">GroupBy （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="1911b-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="1911b-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="1911b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
