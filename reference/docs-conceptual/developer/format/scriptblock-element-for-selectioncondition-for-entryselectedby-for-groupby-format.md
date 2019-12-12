---
title: GroupBy 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e01344bd-ad69-4789-8e9f-2e79880c3a33
caps.latest.revision: 6
ms.openlocfilehash: cb79fb942111cee89c6b2abba75de4c494082b7e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368597"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="6c919-102">GroupBy 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="6c919-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="6c919-103">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="6c919-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="6c919-104">當此腳本評估為 `true`時，就會符合條件，並使用定義。</span><span class="sxs-lookup"><span data-stu-id="6c919-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="6c919-105">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="6c919-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="6c919-106">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（format） CustomEntries 專案的 groupby （format） CustomControl 元素，適用于的 CustomControl for GroupBy （format） CustomEntry 元素適用于 CustomEntry 之 groupby （format） SelectionCondition 元素的 GroupBy （format）之 entryselectedby 元素的 CustomControl，適用于之 entryselectedby 的 groupby （format） ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6c919-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6c919-107">語法</span><span class="sxs-lookup"><span data-stu-id="6c919-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6c919-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="6c919-108">Attributes and Elements</span></span>

<span data-ttu-id="6c919-109">下列各節說明屬性、子專案，以及 `ScriptBlock` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="6c919-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6c919-110">屬性</span><span class="sxs-lookup"><span data-stu-id="6c919-110">Attributes</span></span>

<span data-ttu-id="6c919-111">無。</span><span class="sxs-lookup"><span data-stu-id="6c919-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6c919-112">子元素</span><span class="sxs-lookup"><span data-stu-id="6c919-112">Child Elements</span></span>

<span data-ttu-id="6c919-113">無。</span><span class="sxs-lookup"><span data-stu-id="6c919-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6c919-114">父元素</span><span class="sxs-lookup"><span data-stu-id="6c919-114">Parent Elements</span></span>

|<span data-ttu-id="6c919-115">元素</span><span class="sxs-lookup"><span data-stu-id="6c919-115">Element</span></span>|<span data-ttu-id="6c919-116">描述</span><span class="sxs-lookup"><span data-stu-id="6c919-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6c919-117">GroupBy 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6c919-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="6c919-118">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="6c919-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6c919-119">文字值</span><span class="sxs-lookup"><span data-stu-id="6c919-119">Text Value</span></span>

<span data-ttu-id="6c919-120">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="6c919-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="6c919-121">備註</span><span class="sxs-lookup"><span data-stu-id="6c919-121">Remarks</span></span>

<span data-ttu-id="6c919-122">選取條件必須指定至少一個要評估的腳本或屬性名稱，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="6c919-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="6c919-123">如需如何使用選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="6c919-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6c919-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c919-124">See Also</span></span>

[<span data-ttu-id="6c919-125">GroupBy 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6c919-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="6c919-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="6c919-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
