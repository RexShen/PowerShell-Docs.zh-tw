---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 ItemSelectionCondition 的 PropertyName 元素 (格式)
description: 設定之控制項的 ItemSelectionCondition 的 PropertyName 元素 (格式)
ms.openlocfilehash: 860683eb54b2a3579767640c1d3f0937897b8f8e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655137"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="64f9a-103">設定之控制項的 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="64f9a-103">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="64f9a-104">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="64f9a-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="64f9a-105">當這個屬性存在或評估為時，就 `true` 會符合條件，並且會使用控制項。</span><span class="sxs-lookup"><span data-stu-id="64f9a-105">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="64f9a-106">當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="64f9a-106">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="64f9a-107">設定元素 (格式) 控制項的設定元素 (格式) 控制項的設定 (格式) CustomControl 專案的設定 (格式) CustomEntry 專案的 CustomControl 設定 (格式) 元素，用於 CustomControl 的控制項設定 (格式) CustomItem 元素，用於 CustomEntry 控制項的設定 ExpressionBinding 專案 CustomItem 的設定 (格式) ItemSelectionCondition 專案的設定 (格式) 的 ExpressionBinding 控制項設定 (格式) </span><span class="sxs-lookup"><span data-stu-id="64f9a-107">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="64f9a-108">語法</span><span class="sxs-lookup"><span data-stu-id="64f9a-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="64f9a-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="64f9a-109">Attributes and Elements</span></span>

<span data-ttu-id="64f9a-110">下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="64f9a-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="64f9a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="64f9a-111">Attributes</span></span>

<span data-ttu-id="64f9a-112">無。</span><span class="sxs-lookup"><span data-stu-id="64f9a-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="64f9a-113">子元素</span><span class="sxs-lookup"><span data-stu-id="64f9a-113">Child Elements</span></span>

<span data-ttu-id="64f9a-114">無。</span><span class="sxs-lookup"><span data-stu-id="64f9a-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="64f9a-115">父項目</span><span class="sxs-lookup"><span data-stu-id="64f9a-115">Parent Elements</span></span>

|<span data-ttu-id="64f9a-116">元素</span><span class="sxs-lookup"><span data-stu-id="64f9a-116">Element</span></span>|<span data-ttu-id="64f9a-117">描述</span><span class="sxs-lookup"><span data-stu-id="64f9a-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="64f9a-118">設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="64f9a-118">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="64f9a-119">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="64f9a-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="64f9a-120">文字值</span><span class="sxs-lookup"><span data-stu-id="64f9a-120">Text Value</span></span>

<span data-ttu-id="64f9a-121">指定觸發條件的 .NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="64f9a-121">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="64f9a-122">備註</span><span class="sxs-lookup"><span data-stu-id="64f9a-122">Remarks</span></span>

<span data-ttu-id="64f9a-123">如果使用此元素，則在定義選取條件時，不能指定 [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="64f9a-123">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="64f9a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64f9a-124">See Also</span></span>

[<span data-ttu-id="64f9a-125">設定之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="64f9a-125">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="64f9a-126">設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="64f9a-126">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="64f9a-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="64f9a-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
