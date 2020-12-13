---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的 SelectionCondition 的 ScriptBlock 元素 (格式)
description: 檢視之控制項的 SelectionCondition 的 ScriptBlock 元素 (格式)
ms.openlocfilehash: 7eed3b8a06bc45396026b8e2a7454447b3090d74
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664936"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="19f8d-103">檢視之控制項的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="19f8d-103">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="19f8d-104">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="19f8d-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="19f8d-105">當此腳本評估為時 `true` ，就會符合條件，並使用定義。</span><span class="sxs-lookup"><span data-stu-id="19f8d-105">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="19f8d-106">當定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="19f8d-106">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="19f8d-107">設定元素 (格式) ViewDefinitions 元素 (格式) View 專案 (格式) 控制項專案 (格式) 控制項專案 (格式) 控制項控制項的控制項 (格式) CustomEntries 元素，用於控制項的視圖 (格式) 適用于 view 的控制項之 CustomEntries 的 CustomEntry 專案 (格式) 之 entryselectedby 專案 CustomEntry 的控制項視圖 (格式) SelectionCondition 專案適用于之 entryselectedby 的控制項 (格式) </span><span class="sxs-lookup"><span data-stu-id="19f8d-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="19f8d-108">語法</span><span class="sxs-lookup"><span data-stu-id="19f8d-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="19f8d-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="19f8d-109">Attributes and Elements</span></span>

<span data-ttu-id="19f8d-110">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="19f8d-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="19f8d-111">屬性</span><span class="sxs-lookup"><span data-stu-id="19f8d-111">Attributes</span></span>

<span data-ttu-id="19f8d-112">無。</span><span class="sxs-lookup"><span data-stu-id="19f8d-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="19f8d-113">子元素</span><span class="sxs-lookup"><span data-stu-id="19f8d-113">Child Elements</span></span>

<span data-ttu-id="19f8d-114">無。</span><span class="sxs-lookup"><span data-stu-id="19f8d-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="19f8d-115">父項目</span><span class="sxs-lookup"><span data-stu-id="19f8d-115">Parent Elements</span></span>

|<span data-ttu-id="19f8d-116">元素</span><span class="sxs-lookup"><span data-stu-id="19f8d-116">Element</span></span>|<span data-ttu-id="19f8d-117">描述</span><span class="sxs-lookup"><span data-stu-id="19f8d-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="19f8d-118">檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="19f8d-118">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="19f8d-119">定義必須存在才能使用控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="19f8d-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="19f8d-120">文字值</span><span class="sxs-lookup"><span data-stu-id="19f8d-120">Text Value</span></span>

<span data-ttu-id="19f8d-121">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="19f8d-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="19f8d-122">備註</span><span class="sxs-lookup"><span data-stu-id="19f8d-122">Remarks</span></span>

<span data-ttu-id="19f8d-123">選取條件必須指定至少一個要評估的腳本或屬性名稱，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="19f8d-123">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="19f8d-124">如需如何使用選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="19f8d-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="19f8d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19f8d-125">See Also</span></span>

[<span data-ttu-id="19f8d-126">檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="19f8d-126">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="19f8d-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="19f8d-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
