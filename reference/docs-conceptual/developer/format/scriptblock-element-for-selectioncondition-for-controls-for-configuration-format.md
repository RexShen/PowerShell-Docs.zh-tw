---
title: 設定之控制項的 SelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368617"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="d55d6-102">設定之控制項的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d55d6-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="d55d6-103">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="d55d6-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="d55d6-104">當此腳本評估為 `true` 時，就會符合條件，並使用定義。</span><span class="sxs-lookup"><span data-stu-id="d55d6-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="d55d6-105">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="d55d6-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="d55d6-106">Configuration 元素（格式）控制設定（format） CustomControl 元素的設定（格式）控制項專案的設定專案（格式） CustomControl 設定的 CustomEntries 元素（格式）Format） CustomEntry 元素，用於 CustomControl for 控制項的之 entryselectedby 元素（格式為 CustomEntry 的控制項，適用于 configuration （格式） SelectionCondition 元素的控制項）。設定之控制項的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d55d6-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d55d6-107">語法</span><span class="sxs-lookup"><span data-stu-id="d55d6-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d55d6-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="d55d6-108">Attributes and Elements</span></span>

<span data-ttu-id="d55d6-109">下列各節說明屬性、子專案，以及 `ScriptBlock` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="d55d6-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d55d6-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d55d6-110">Attributes</span></span>

<span data-ttu-id="d55d6-111">無。</span><span class="sxs-lookup"><span data-stu-id="d55d6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d55d6-112">子元素</span><span class="sxs-lookup"><span data-stu-id="d55d6-112">Child Elements</span></span>

<span data-ttu-id="d55d6-113">無。</span><span class="sxs-lookup"><span data-stu-id="d55d6-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d55d6-114">父元素</span><span class="sxs-lookup"><span data-stu-id="d55d6-114">Parent Elements</span></span>

|<span data-ttu-id="d55d6-115">元素</span><span class="sxs-lookup"><span data-stu-id="d55d6-115">Element</span></span>|<span data-ttu-id="d55d6-116">描述</span><span class="sxs-lookup"><span data-stu-id="d55d6-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d55d6-117">設定之控制項的之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d55d6-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="d55d6-118">定義必須存在的條件，才能使用通用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="d55d6-118">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d55d6-119">文字值</span><span class="sxs-lookup"><span data-stu-id="d55d6-119">Text Value</span></span>

<span data-ttu-id="d55d6-120">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="d55d6-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="d55d6-121">備註</span><span class="sxs-lookup"><span data-stu-id="d55d6-121">Remarks</span></span>

<span data-ttu-id="d55d6-122">選取條件必須指定至少一個要評估的腳本或屬性名稱，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="d55d6-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="d55d6-123">如需如何使用選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="d55d6-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d55d6-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d55d6-124">See Also</span></span>

[<span data-ttu-id="d55d6-125">設定之控制項的之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d55d6-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="d55d6-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="d55d6-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
