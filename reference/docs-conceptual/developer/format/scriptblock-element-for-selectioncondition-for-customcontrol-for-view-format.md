---
title: SelectionCondition for CustomControl for View (Format) 的 ScriptBlock 元素Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d3506188d32ce85ad6345dc0d0866dd789a1f293
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785399"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="1769c-102">檢視之 CustomControl 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1769c-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="1769c-103">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="1769c-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="1769c-104">當此腳本評估為時 `true` ，會符合條件，並使用定義。</span><span class="sxs-lookup"><span data-stu-id="1769c-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="1769c-105">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="1769c-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="1769c-106">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) CustomControl for view (格式的 CustomEntries 專案) 格式 (CustomEntry for CustomEntries for view) CustomControl 元素的 CustomItem for CustomEntry for view (format) CustomControl 元素 for SelectionCondition for view (格式) 之 entryselectedby 元素（CustomControl for SelectionCondition for view (format) ScriptBlock 元素） (</span><span class="sxs-lookup"><span data-stu-id="1769c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1769c-107">語法</span><span class="sxs-lookup"><span data-stu-id="1769c-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1769c-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1769c-108">Attributes and Elements</span></span>

<span data-ttu-id="1769c-109">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="1769c-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1769c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="1769c-110">Attributes</span></span>

<span data-ttu-id="1769c-111">無。</span><span class="sxs-lookup"><span data-stu-id="1769c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1769c-112">子元素</span><span class="sxs-lookup"><span data-stu-id="1769c-112">Child Elements</span></span>

<span data-ttu-id="1769c-113">無。</span><span class="sxs-lookup"><span data-stu-id="1769c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1769c-114">父項目</span><span class="sxs-lookup"><span data-stu-id="1769c-114">Parent Elements</span></span>

|<span data-ttu-id="1769c-115">元素</span><span class="sxs-lookup"><span data-stu-id="1769c-115">Element</span></span>|<span data-ttu-id="1769c-116">描述</span><span class="sxs-lookup"><span data-stu-id="1769c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1769c-117">CustomControl for View (格式) 的之 entryselectedby 的 SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="1769c-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="1769c-118">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="1769c-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1769c-119">文字值</span><span class="sxs-lookup"><span data-stu-id="1769c-119">Text Value</span></span>

<span data-ttu-id="1769c-120">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="1769c-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="1769c-121">備註</span><span class="sxs-lookup"><span data-stu-id="1769c-121">Remarks</span></span>

<span data-ttu-id="1769c-122">選取條件必須指定至少一個要評估的腳本或屬性名稱，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="1769c-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="1769c-123">如需如何使用選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="1769c-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1769c-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1769c-124">See Also</span></span>

[<span data-ttu-id="1769c-125">CustomControl for View (格式) 的之 entryselectedby 的 SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="1769c-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="1769c-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="1769c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
