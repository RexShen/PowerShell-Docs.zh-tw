---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)
description: 檢視之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)
ms.openlocfilehash: c005215f7b7984541806d2f5de47372d536787ff
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665194"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="2ef1b-103">檢視之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2ef1b-103">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="2ef1b-104">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="2ef1b-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="2ef1b-105">當此腳本評估為時 `true` ，就會符合條件，並且會使用控制項。</span><span class="sxs-lookup"><span data-stu-id="2ef1b-105">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="2ef1b-106">當定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="2ef1b-106">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="2ef1b-107">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) Control 元素 (format) Control 元素 (format) format 控制項 for view (format) CustomEntries 元素 for view (format) format CustomEntry 元素 for CustomEntries 針對 view 的控制項 (格式) CustomItem 專案適用于視圖的控制項 (格式) ExpressionBinding 專案 CustomItem 的專案 (格式)  (格式控制項的 ItemSelectionCondition 專案)  (格式) 的控制項的 ExpressionBinding 元素</span><span class="sxs-lookup"><span data-stu-id="2ef1b-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2ef1b-108">語法</span><span class="sxs-lookup"><span data-stu-id="2ef1b-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2ef1b-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2ef1b-109">Attributes and Elements</span></span>

<span data-ttu-id="2ef1b-110">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="2ef1b-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2ef1b-111">屬性</span><span class="sxs-lookup"><span data-stu-id="2ef1b-111">Attributes</span></span>

<span data-ttu-id="2ef1b-112">無。</span><span class="sxs-lookup"><span data-stu-id="2ef1b-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2ef1b-113">子元素</span><span class="sxs-lookup"><span data-stu-id="2ef1b-113">Child Elements</span></span>

<span data-ttu-id="2ef1b-114">無。</span><span class="sxs-lookup"><span data-stu-id="2ef1b-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2ef1b-115">父項目</span><span class="sxs-lookup"><span data-stu-id="2ef1b-115">Parent Elements</span></span>

|<span data-ttu-id="2ef1b-116">元素</span><span class="sxs-lookup"><span data-stu-id="2ef1b-116">Element</span></span>|<span data-ttu-id="2ef1b-117">描述</span><span class="sxs-lookup"><span data-stu-id="2ef1b-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2ef1b-118">View (Format) 的控制項之 ExpressionBinding 元素 ItemSelectionCondition </span><span class="sxs-lookup"><span data-stu-id="2ef1b-118">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="2ef1b-119">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="2ef1b-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2ef1b-120">文字值</span><span class="sxs-lookup"><span data-stu-id="2ef1b-120">Text Value</span></span>

<span data-ttu-id="2ef1b-121">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="2ef1b-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="2ef1b-122">備註</span><span class="sxs-lookup"><span data-stu-id="2ef1b-122">Remarks</span></span>

<span data-ttu-id="2ef1b-123">如果使用此元素，則在定義選取條件時，不能指定 [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="2ef1b-123">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ef1b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ef1b-124">See Also</span></span>

[<span data-ttu-id="2ef1b-125">檢視之控制項的 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2ef1b-125">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="2ef1b-126">View (Format) 的控制項之 ExpressionBinding 元素 ItemSelectionCondition </span><span class="sxs-lookup"><span data-stu-id="2ef1b-126">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="2ef1b-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="2ef1b-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
