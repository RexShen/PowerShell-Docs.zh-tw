---
title: SelectionCondition CustomControl 檢視 （格式） 的指令碼區塊項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857414"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="9abe6-102">檢視之 CustomControl 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9abe6-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="9abe6-103">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="9abe6-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="9abe6-104">此指令碼會評估為`true`、 符合條件，和在使用定義。</span><span class="sxs-lookup"><span data-stu-id="9abe6-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="9abe6-105">定義自訂控制項的檢視時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="9abe6-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="9abe6-106">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目進行檢視 （格式） 的檢視 （如 CustomControl CustomEntries CustomEntry 元素 CustomControl 的檢視 （格式） CustomEntries 項目格式） 的檢視 （格式） SelectionCondition 項目，如 CustomControl SelectionCondition CustomControl 檢視 （格式） 的檢視 （格式） ScriptBlock 元素的 EntrySelectedBy CustomControl CustomEntry CustomItem 項目</span><span class="sxs-lookup"><span data-stu-id="9abe6-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9abe6-107">語法</span><span class="sxs-lookup"><span data-stu-id="9abe6-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9abe6-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="9abe6-108">Attributes and Elements</span></span>

<span data-ttu-id="9abe6-109">下列各節說明屬性、 子項目和父項目`ScriptBlock`項目。</span><span class="sxs-lookup"><span data-stu-id="9abe6-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9abe6-110">屬性</span><span class="sxs-lookup"><span data-stu-id="9abe6-110">Attributes</span></span>

<span data-ttu-id="9abe6-111">無。</span><span class="sxs-lookup"><span data-stu-id="9abe6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9abe6-112">子元素</span><span class="sxs-lookup"><span data-stu-id="9abe6-112">Child Elements</span></span>

<span data-ttu-id="9abe6-113">無。</span><span class="sxs-lookup"><span data-stu-id="9abe6-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9abe6-114">父元素</span><span class="sxs-lookup"><span data-stu-id="9abe6-114">Parent Elements</span></span>

|<span data-ttu-id="9abe6-115">元素</span><span class="sxs-lookup"><span data-stu-id="9abe6-115">Element</span></span>|<span data-ttu-id="9abe6-116">描述</span><span class="sxs-lookup"><span data-stu-id="9abe6-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9abe6-117">CustomControl 檢視 （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="9abe6-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="9abe6-118">定義必須存在，要使用的控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="9abe6-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9abe6-119">文字值</span><span class="sxs-lookup"><span data-stu-id="9abe6-119">Text Value</span></span>

<span data-ttu-id="9abe6-120">指定評估指令碼。</span><span class="sxs-lookup"><span data-stu-id="9abe6-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="9abe6-121">備註</span><span class="sxs-lookup"><span data-stu-id="9abe6-121">Remarks</span></span>

<span data-ttu-id="9abe6-122">選取條件必須指定至少一個指令碼或屬性名稱來評估，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="9abe6-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="9abe6-123">如需如何使用選擇條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="9abe6-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9abe6-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9abe6-124">See Also</span></span>

[<span data-ttu-id="9abe6-125">CustomControl 檢視 （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="9abe6-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="9abe6-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="9abe6-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
