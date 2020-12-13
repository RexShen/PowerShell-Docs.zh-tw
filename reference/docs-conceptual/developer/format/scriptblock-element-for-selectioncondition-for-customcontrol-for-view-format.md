---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之 CustomControl 的 SelectionCondition 的 ScriptBlock 元素 (格式)
description: 檢視之 CustomControl 的 SelectionCondition 的 ScriptBlock 元素 (格式)
ms.openlocfilehash: 78b977548243b6f3a658f15a0249d8cad12e2f1b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664919"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="4ff41-103">檢視之 CustomControl 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4ff41-103">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="4ff41-104">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="4ff41-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="4ff41-105">當此腳本評估為時 `true` ，就會符合條件，並使用定義。</span><span class="sxs-lookup"><span data-stu-id="4ff41-105">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="4ff41-106">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="4ff41-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="4ff41-107">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) CustomEntries 元素 for View (Format) 元素 for CustomControl for View (format) 元素 for CustomEntry for CustomEntries for CustomControl for view (format) CustomItem 專案 for CustomEntry for CustomControl for view (format) SelectionCondition for 之 entryselectedby for CustomControl 的 SelectionCondition 專案 (格式) </span><span class="sxs-lookup"><span data-stu-id="4ff41-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4ff41-108">語法</span><span class="sxs-lookup"><span data-stu-id="4ff41-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4ff41-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4ff41-109">Attributes and Elements</span></span>

<span data-ttu-id="4ff41-110">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="4ff41-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4ff41-111">屬性</span><span class="sxs-lookup"><span data-stu-id="4ff41-111">Attributes</span></span>

<span data-ttu-id="4ff41-112">無。</span><span class="sxs-lookup"><span data-stu-id="4ff41-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4ff41-113">子元素</span><span class="sxs-lookup"><span data-stu-id="4ff41-113">Child Elements</span></span>

<span data-ttu-id="4ff41-114">無。</span><span class="sxs-lookup"><span data-stu-id="4ff41-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4ff41-115">父項目</span><span class="sxs-lookup"><span data-stu-id="4ff41-115">Parent Elements</span></span>

|<span data-ttu-id="4ff41-116">元素</span><span class="sxs-lookup"><span data-stu-id="4ff41-116">Element</span></span>|<span data-ttu-id="4ff41-117">描述</span><span class="sxs-lookup"><span data-stu-id="4ff41-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4ff41-118">適用于 CustomControl 的之 entryselectedby SelectionCondition 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="4ff41-118">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="4ff41-119">定義必須存在才能使用控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="4ff41-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4ff41-120">文字值</span><span class="sxs-lookup"><span data-stu-id="4ff41-120">Text Value</span></span>

<span data-ttu-id="4ff41-121">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="4ff41-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="4ff41-122">備註</span><span class="sxs-lookup"><span data-stu-id="4ff41-122">Remarks</span></span>

<span data-ttu-id="4ff41-123">選取條件必須指定至少一個要評估的腳本或屬性名稱，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="4ff41-123">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="4ff41-124">如需如何使用選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="4ff41-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4ff41-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ff41-125">See Also</span></span>

[<span data-ttu-id="4ff41-126">適用于 CustomControl 的之 entryselectedby SelectionCondition 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="4ff41-126">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="4ff41-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="4ff41-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
