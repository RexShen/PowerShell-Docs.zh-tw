---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)
description: 設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)
ms.openlocfilehash: 1abcf2173e18d45839161b4c7e59f1ad238f81a1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655328"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="e75bc-103">設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e75bc-103">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e75bc-104">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="e75bc-104">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="e75bc-105">當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="e75bc-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e75bc-106">設定專案 (格式) 控制項的設定專案 (格式設定的控制項) 控制項專案 (格式) CustomEntries 專案的 CustomControl 設定 (格式) CustomControl 專案的設定 (格式) CustomItem 專案的設定 (格式) CustomEntry 專案的設定 (格式) 的控制項設定 ExpressionBinding 專案的 CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="e75bc-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e75bc-107">語法</span><span class="sxs-lookup"><span data-stu-id="e75bc-107">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e75bc-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e75bc-108">Attributes and Elements</span></span>

<span data-ttu-id="e75bc-109">下列各節說明屬性、子專案和元素的父元素 `ExpressionBinding` 。</span><span class="sxs-lookup"><span data-stu-id="e75bc-109">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e75bc-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e75bc-110">Attributes</span></span>

<span data-ttu-id="e75bc-111">無。</span><span class="sxs-lookup"><span data-stu-id="e75bc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e75bc-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e75bc-112">Child Elements</span></span>

|<span data-ttu-id="e75bc-113">元素</span><span class="sxs-lookup"><span data-stu-id="e75bc-113">Element</span></span>|<span data-ttu-id="e75bc-114">描述</span><span class="sxs-lookup"><span data-stu-id="e75bc-114">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="e75bc-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e75bc-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e75bc-116">定義這個控制項所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="e75bc-116">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="e75bc-117">設定之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e75bc-117">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e75bc-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e75bc-118">Optional element.</span></span><br /><br /> <span data-ttu-id="e75bc-119">指定通用控制項或 view 控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="e75bc-119">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="e75bc-120">設定之控制項的 ExpressionBinding 的 EnumerateCollection 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e75bc-120">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e75bc-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e75bc-121">Optional element.</span></span><br /><br /> <span data-ttu-id="e75bc-122">指定控制項會顯示集合的元素。</span><span class="sxs-lookup"><span data-stu-id="e75bc-122">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="e75bc-123">設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e75bc-123">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e75bc-124">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e75bc-124">Optional element.</span></span><br /><br /> <span data-ttu-id="e75bc-125">定義必須存在才能使用此通用控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="e75bc-125">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="e75bc-126">設定之控制項的 ExpressionBinding 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e75bc-126">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e75bc-127">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e75bc-127">Optional element.</span></span><br /><br /> <span data-ttu-id="e75bc-128">指定由通用控制項顯示其值的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="e75bc-128">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="e75bc-129">設定之控制項的 ExpressionBinding 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e75bc-129">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e75bc-130">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e75bc-130">Optional element.</span></span><br /><br /> <span data-ttu-id="e75bc-131">指定由通用控制項顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="e75bc-131">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e75bc-132">父項目</span><span class="sxs-lookup"><span data-stu-id="e75bc-132">Parent Elements</span></span>

|<span data-ttu-id="e75bc-133">元素</span><span class="sxs-lookup"><span data-stu-id="e75bc-133">Element</span></span>|<span data-ttu-id="e75bc-134">描述</span><span class="sxs-lookup"><span data-stu-id="e75bc-134">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e75bc-135">適用于設定之控制項的 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="e75bc-135">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="e75bc-136">定義自訂控制項視圖所顯示的資料，以及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="e75bc-136">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e75bc-137">備註</span><span class="sxs-lookup"><span data-stu-id="e75bc-137">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="e75bc-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e75bc-138">See Also</span></span>

[<span data-ttu-id="e75bc-139">適用于設定之控制項的 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="e75bc-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="e75bc-140">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="e75bc-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
