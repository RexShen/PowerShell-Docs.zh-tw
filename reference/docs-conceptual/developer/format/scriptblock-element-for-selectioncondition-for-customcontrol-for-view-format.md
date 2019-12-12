---
title: CustomControl for View 的 SelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368637"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="d0b03-102">檢視之 CustomControl 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d0b03-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="d0b03-103">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="d0b03-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="d0b03-104">當此腳本評估為 `true`時，就會符合條件，並使用定義。</span><span class="sxs-lookup"><span data-stu-id="d0b03-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="d0b03-105">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="d0b03-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="d0b03-106">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素 for view （format） CustomEntries 元素 for CustomEntry for view （format） CustomEntries 元素Format） CustomItem 元素，用於 CustomControl for view （format） SelectionCondition 元素，之 entryselectedby for CustomControl for view （format） ScriptBlock 元素 for SelectionCondition for view （格式） CustomControl</span><span class="sxs-lookup"><span data-stu-id="d0b03-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d0b03-107">語法</span><span class="sxs-lookup"><span data-stu-id="d0b03-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d0b03-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="d0b03-108">Attributes and Elements</span></span>

<span data-ttu-id="d0b03-109">下列各節說明屬性、子專案，以及 `ScriptBlock` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="d0b03-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d0b03-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d0b03-110">Attributes</span></span>

<span data-ttu-id="d0b03-111">無。</span><span class="sxs-lookup"><span data-stu-id="d0b03-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d0b03-112">子元素</span><span class="sxs-lookup"><span data-stu-id="d0b03-112">Child Elements</span></span>

<span data-ttu-id="d0b03-113">無。</span><span class="sxs-lookup"><span data-stu-id="d0b03-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d0b03-114">父元素</span><span class="sxs-lookup"><span data-stu-id="d0b03-114">Parent Elements</span></span>

|<span data-ttu-id="d0b03-115">元素</span><span class="sxs-lookup"><span data-stu-id="d0b03-115">Element</span></span>|<span data-ttu-id="d0b03-116">描述</span><span class="sxs-lookup"><span data-stu-id="d0b03-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0b03-117">CustomControl for View 的之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d0b03-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="d0b03-118">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="d0b03-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d0b03-119">文字值</span><span class="sxs-lookup"><span data-stu-id="d0b03-119">Text Value</span></span>

<span data-ttu-id="d0b03-120">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="d0b03-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0b03-121">備註</span><span class="sxs-lookup"><span data-stu-id="d0b03-121">Remarks</span></span>

<span data-ttu-id="d0b03-122">選取條件必須指定至少一個要評估的腳本或屬性名稱，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="d0b03-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="d0b03-123">如需如何使用選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="d0b03-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d0b03-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0b03-124">See Also</span></span>

[<span data-ttu-id="d0b03-125">CustomControl for View 的之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d0b03-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="d0b03-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="d0b03-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
