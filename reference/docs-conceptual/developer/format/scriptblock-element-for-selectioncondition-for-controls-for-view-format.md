---
title: View (Format) 之控制項的 SelectionCondition 的 ScriptBlock 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e5f4295a989307cb6ffb655c2c39596f3d1ea806
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785416"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="83a4d-102">檢視之控制項的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="83a4d-102">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="83a4d-103">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="83a4d-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="83a4d-104">當此腳本評估為時 `true` ，會符合條件，並使用定義。</span><span class="sxs-lookup"><span data-stu-id="83a4d-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="83a4d-105">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="83a4d-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="83a4d-106">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 CustomControl 格式 (CustomEntries 元素用於 view 的控制項)  ( (格式) 的控制項適用于 CustomEntries 的 CustomEntry 元素，用於 view (Format) 之 entryselectedby 專案 CustomEntry for view (format) SelectionCondition 元素 for view (format) ScriptBlock 元素 for view (format 的控制項) </span><span class="sxs-lookup"><span data-stu-id="83a4d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="83a4d-107">語法</span><span class="sxs-lookup"><span data-stu-id="83a4d-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="83a4d-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="83a4d-108">Attributes and Elements</span></span>

<span data-ttu-id="83a4d-109">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="83a4d-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="83a4d-110">屬性</span><span class="sxs-lookup"><span data-stu-id="83a4d-110">Attributes</span></span>

<span data-ttu-id="83a4d-111">無。</span><span class="sxs-lookup"><span data-stu-id="83a4d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="83a4d-112">子元素</span><span class="sxs-lookup"><span data-stu-id="83a4d-112">Child Elements</span></span>

<span data-ttu-id="83a4d-113">無。</span><span class="sxs-lookup"><span data-stu-id="83a4d-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="83a4d-114">父項目</span><span class="sxs-lookup"><span data-stu-id="83a4d-114">Parent Elements</span></span>

|<span data-ttu-id="83a4d-115">元素</span><span class="sxs-lookup"><span data-stu-id="83a4d-115">Element</span></span>|<span data-ttu-id="83a4d-116">描述</span><span class="sxs-lookup"><span data-stu-id="83a4d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="83a4d-117">檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="83a4d-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="83a4d-118">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="83a4d-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="83a4d-119">文字值</span><span class="sxs-lookup"><span data-stu-id="83a4d-119">Text Value</span></span>

<span data-ttu-id="83a4d-120">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="83a4d-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="83a4d-121">備註</span><span class="sxs-lookup"><span data-stu-id="83a4d-121">Remarks</span></span>

<span data-ttu-id="83a4d-122">選取條件必須指定至少一個要評估的腳本或屬性名稱，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="83a4d-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="83a4d-123">如需如何使用選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="83a4d-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="83a4d-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83a4d-124">See Also</span></span>

[<span data-ttu-id="83a4d-125">檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="83a4d-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="83a4d-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="83a4d-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
