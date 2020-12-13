---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)
description: 設定之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)
ms.openlocfilehash: 853130da4489e571d7f4026a8d65d029d1889f9b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665219"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="0c0fd-103">設定之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0c0fd-103">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="0c0fd-104">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="0c0fd-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="0c0fd-105">當此腳本評估為時 `true` ，就會符合條件，並且會使用控制項。</span><span class="sxs-lookup"><span data-stu-id="0c0fd-105">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="0c0fd-106">當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="0c0fd-106">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="0c0fd-107">設定元素 (格式) 控制項的設定元素 (格式) 控制項的設定 (格式) CustomControl 專案的設定 (格式) CustomEntry 專案的 CustomControl 設定 (格式) 元素，用於 CustomControl 的控制項設定 (格式) CustomItem 元素，適用于 CustomEntry 的設定 ExpressionBinding 專案設定專案 CustomItem 的設定 (格式) ItemSelectionCondition 專案設定 (格式) ScriptBlock 專案的 ExpressionBinding 控制項設定 (格式) </span><span class="sxs-lookup"><span data-stu-id="0c0fd-107">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0c0fd-108">語法</span><span class="sxs-lookup"><span data-stu-id="0c0fd-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0c0fd-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0c0fd-109">Attributes and Elements</span></span>

<span data-ttu-id="0c0fd-110">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="0c0fd-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0c0fd-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0c0fd-111">Attributes</span></span>

<span data-ttu-id="0c0fd-112">無。</span><span class="sxs-lookup"><span data-stu-id="0c0fd-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0c0fd-113">子元素</span><span class="sxs-lookup"><span data-stu-id="0c0fd-113">Child Elements</span></span>

<span data-ttu-id="0c0fd-114">無。</span><span class="sxs-lookup"><span data-stu-id="0c0fd-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0c0fd-115">父項目</span><span class="sxs-lookup"><span data-stu-id="0c0fd-115">Parent Elements</span></span>

|<span data-ttu-id="0c0fd-116">元素</span><span class="sxs-lookup"><span data-stu-id="0c0fd-116">Element</span></span>|<span data-ttu-id="0c0fd-117">描述</span><span class="sxs-lookup"><span data-stu-id="0c0fd-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0c0fd-118">設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0c0fd-118">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="0c0fd-119">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="0c0fd-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0c0fd-120">文字值</span><span class="sxs-lookup"><span data-stu-id="0c0fd-120">Text Value</span></span>

<span data-ttu-id="0c0fd-121">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="0c0fd-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="0c0fd-122">備註</span><span class="sxs-lookup"><span data-stu-id="0c0fd-122">Remarks</span></span>

<span data-ttu-id="0c0fd-123">如果使用此元素，則在定義選取條件時，不能指定 [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="0c0fd-123">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c0fd-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c0fd-124">See Also</span></span>

[<span data-ttu-id="0c0fd-125">設定之控制項的 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0c0fd-125">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="0c0fd-126">設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0c0fd-126">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="0c0fd-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="0c0fd-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
