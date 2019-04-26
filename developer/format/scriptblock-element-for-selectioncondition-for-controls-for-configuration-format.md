---
title: ScriptBlock SelectionCondition 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064419"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="26679-102">設定之控制項的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="26679-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="26679-103">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="26679-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="26679-104">此指令碼會評估為`true`、 符合條件，和在使用定義。</span><span class="sxs-lookup"><span data-stu-id="26679-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="26679-105">定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="26679-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="26679-106">組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目CustomControl CustomEntry EntrySelectedBy 控制項組態 （格式） 的組態 （格式） SelectionCondition 元素的控制項的組態 （格式） EntrySelectedBy 元素的控制項的格式） CustomEntry 項目ScriptBlock SelectionCondition 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="26679-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="26679-107">語法</span><span class="sxs-lookup"><span data-stu-id="26679-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="26679-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="26679-108">Attributes and Elements</span></span>

<span data-ttu-id="26679-109">下列各節說明屬性、 子項目和父項目`ScriptBlock`項目。</span><span class="sxs-lookup"><span data-stu-id="26679-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="26679-110">屬性</span><span class="sxs-lookup"><span data-stu-id="26679-110">Attributes</span></span>

<span data-ttu-id="26679-111">無。</span><span class="sxs-lookup"><span data-stu-id="26679-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="26679-112">子元素</span><span class="sxs-lookup"><span data-stu-id="26679-112">Child Elements</span></span>

<span data-ttu-id="26679-113">無。</span><span class="sxs-lookup"><span data-stu-id="26679-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="26679-114">父項目</span><span class="sxs-lookup"><span data-stu-id="26679-114">Parent Elements</span></span>

|<span data-ttu-id="26679-115">項目</span><span class="sxs-lookup"><span data-stu-id="26679-115">Element</span></span>|<span data-ttu-id="26679-116">描述</span><span class="sxs-lookup"><span data-stu-id="26679-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="26679-117">SelectionCondition EntrySelectedBy 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="26679-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="26679-118">定義必須存在通用控制項定義要使用的條件。</span><span class="sxs-lookup"><span data-stu-id="26679-118">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="26679-119">文字值</span><span class="sxs-lookup"><span data-stu-id="26679-119">Text Value</span></span>

<span data-ttu-id="26679-120">指定評估指令碼。</span><span class="sxs-lookup"><span data-stu-id="26679-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="26679-121">備註</span><span class="sxs-lookup"><span data-stu-id="26679-121">Remarks</span></span>

<span data-ttu-id="26679-122">選取條件必須指定至少一個指令碼或屬性名稱來評估，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="26679-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="26679-123">如需如何使用選擇條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="26679-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="26679-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26679-124">See Also</span></span>

[<span data-ttu-id="26679-125">SelectionCondition EntrySelectedBy 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="26679-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="26679-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="26679-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
