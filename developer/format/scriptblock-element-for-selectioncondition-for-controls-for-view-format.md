---
title: 用於檢視 （格式） 的控制項 SelectionCondition 的指令碼區塊項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08512496-5682-4539-ab56-0c5394ce1f01
caps.latest.revision: 6
ms.openlocfilehash: 0137886437f01518f396613c564517e7910e657a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861834"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="32321-102">檢視之控制項的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="32321-102">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="32321-103">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="32321-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="32321-104">此指令碼會評估為`true`、 符合條件，和在使用定義。</span><span class="sxs-lookup"><span data-stu-id="32321-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="32321-105">定義可供檢視的控制項時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="32321-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="32321-106">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目CustomControl CustomEntries CustomEntry EntrySelectedBy 的檢視 （控制項的檢視 （格式） SelectionCondition 元素的控制項的檢視 （格式） EntrySelectedBy 元素的控制項的檢視 （格式） CustomEntry 元素的控制項用於檢視 （格式） 的控制項 SelectionCondition 的格式） 指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="32321-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="32321-107">語法</span><span class="sxs-lookup"><span data-stu-id="32321-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="32321-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="32321-108">Attributes and Elements</span></span>

<span data-ttu-id="32321-109">下列各節說明屬性、 子項目和父項目`ScriptBlock`項目。</span><span class="sxs-lookup"><span data-stu-id="32321-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="32321-110">屬性</span><span class="sxs-lookup"><span data-stu-id="32321-110">Attributes</span></span>

<span data-ttu-id="32321-111">無。</span><span class="sxs-lookup"><span data-stu-id="32321-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="32321-112">子元素</span><span class="sxs-lookup"><span data-stu-id="32321-112">Child Elements</span></span>

<span data-ttu-id="32321-113">無。</span><span class="sxs-lookup"><span data-stu-id="32321-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="32321-114">父元素</span><span class="sxs-lookup"><span data-stu-id="32321-114">Parent Elements</span></span>

|<span data-ttu-id="32321-115">元素</span><span class="sxs-lookup"><span data-stu-id="32321-115">Element</span></span>|<span data-ttu-id="32321-116">描述</span><span class="sxs-lookup"><span data-stu-id="32321-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="32321-117">用於檢視 （格式） 的控制項 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="32321-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="32321-118">定義必須存在，要使用的控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="32321-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="32321-119">文字值</span><span class="sxs-lookup"><span data-stu-id="32321-119">Text Value</span></span>

<span data-ttu-id="32321-120">指定評估指令碼。</span><span class="sxs-lookup"><span data-stu-id="32321-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="32321-121">備註</span><span class="sxs-lookup"><span data-stu-id="32321-121">Remarks</span></span>

<span data-ttu-id="32321-122">選取條件必須指定至少一個指令碼或屬性名稱來評估，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="32321-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="32321-123">如需如何使用選擇條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="32321-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="32321-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32321-124">See Also</span></span>

[<span data-ttu-id="32321-125">用於檢視 （格式） 的控制項 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="32321-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="32321-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="32321-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
