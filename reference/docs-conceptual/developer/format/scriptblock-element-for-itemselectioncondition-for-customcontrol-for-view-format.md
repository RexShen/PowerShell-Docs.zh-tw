---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之 CustomControl 的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)
description: 檢視之 CustomControl 的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)
ms.openlocfilehash: d762f400f5bb52af314093079fe94223c56d3f31
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665131"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="eb5fb-103">檢視之 CustomControl 的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="eb5fb-103">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="eb5fb-104">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="eb5fb-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="eb5fb-105">當此腳本評估為時 `true` ，就會符合條件，並且會使用控制項。</span><span class="sxs-lookup"><span data-stu-id="eb5fb-105">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="eb5fb-106">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="eb5fb-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="eb5fb-107">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) CustomControl 元素 (格式) CustomEntries 元素 (格式)  (格式) CustomEntry 元素適用于 View (格式的 CustomEntry) ExpressionBinding 元素適用于 CustomItem for CustomControl for View (Format) ItemSelectionCondition 元素適用于 CustomControl for View 的運算式系結 (格式) ItemSelectionCondition for CustomControl 的 for view (格式) </span><span class="sxs-lookup"><span data-stu-id="eb5fb-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="eb5fb-108">語法</span><span class="sxs-lookup"><span data-stu-id="eb5fb-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="eb5fb-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="eb5fb-109">Attributes and Elements</span></span>

<span data-ttu-id="eb5fb-110">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="eb5fb-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="eb5fb-111">屬性</span><span class="sxs-lookup"><span data-stu-id="eb5fb-111">Attributes</span></span>

<span data-ttu-id="eb5fb-112">無。</span><span class="sxs-lookup"><span data-stu-id="eb5fb-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="eb5fb-113">子元素</span><span class="sxs-lookup"><span data-stu-id="eb5fb-113">Child Elements</span></span>

<span data-ttu-id="eb5fb-114">無。</span><span class="sxs-lookup"><span data-stu-id="eb5fb-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="eb5fb-115">父項目</span><span class="sxs-lookup"><span data-stu-id="eb5fb-115">Parent Elements</span></span>

|<span data-ttu-id="eb5fb-116">元素</span><span class="sxs-lookup"><span data-stu-id="eb5fb-116">Element</span></span>|<span data-ttu-id="eb5fb-117">描述</span><span class="sxs-lookup"><span data-stu-id="eb5fb-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eb5fb-118">適用于 CustomControl 之 ItemSelectionCondition 運算式系結的元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="eb5fb-118">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="eb5fb-119">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="eb5fb-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="eb5fb-120">文字值</span><span class="sxs-lookup"><span data-stu-id="eb5fb-120">Text Value</span></span>

<span data-ttu-id="eb5fb-121">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="eb5fb-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="eb5fb-122">備註</span><span class="sxs-lookup"><span data-stu-id="eb5fb-122">Remarks</span></span>

<span data-ttu-id="eb5fb-123">如果使用此元素，則在定義選取條件時，不能指定 [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="eb5fb-123">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb5fb-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb5fb-124">See Also</span></span>

[<span data-ttu-id="eb5fb-125">檢視之 CustomControl 的 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="eb5fb-125">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="eb5fb-126">適用于 CustomControl 之 ItemSelectionCondition 運算式系結的元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="eb5fb-126">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="eb5fb-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="eb5fb-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
