---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)
description: GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)
ms.openlocfilehash: 742d9f081a674dc3ee4c84d600933aaf57b2aa6b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655307"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="1b9a7-103">GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1b9a7-103">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="1b9a7-104">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="1b9a7-104">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="1b9a7-105">定義如何顯示新的物件群組時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="1b9a7-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="1b9a7-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 專案 (格式) GroupBy 專案的視圖 (格式) CustomEntries 元素適用于 GroupBy (格式) CustomEntry 專案用於 CustomControl 的 groupby (格式) CustomItem 專案適用于 CustomEntry 的 groupby (格式)  (</span><span class="sxs-lookup"><span data-stu-id="1b9a7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1b9a7-107">語法</span><span class="sxs-lookup"><span data-stu-id="1b9a7-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="1b9a7-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1b9a7-108">Attributes and Elements</span></span>

<span data-ttu-id="1b9a7-109">下列各節說明屬性、子專案和元素的父元素 `ExpressionBinding` 。</span><span class="sxs-lookup"><span data-stu-id="1b9a7-109">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1b9a7-110">屬性</span><span class="sxs-lookup"><span data-stu-id="1b9a7-110">Attributes</span></span>

<span data-ttu-id="1b9a7-111">無。</span><span class="sxs-lookup"><span data-stu-id="1b9a7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1b9a7-112">子元素</span><span class="sxs-lookup"><span data-stu-id="1b9a7-112">Child Elements</span></span>

|<span data-ttu-id="1b9a7-113">元素</span><span class="sxs-lookup"><span data-stu-id="1b9a7-113">Element</span></span>|<span data-ttu-id="1b9a7-114">描述</span><span class="sxs-lookup"><span data-stu-id="1b9a7-114">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="1b9a7-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="1b9a7-115">Optional element.</span></span><br /><br /> <span data-ttu-id="1b9a7-116">定義這個控制項所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="1b9a7-116">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="1b9a7-117">GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1b9a7-117">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="1b9a7-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="1b9a7-118">Optional element.</span></span><br /><br /> <span data-ttu-id="1b9a7-119">指定通用控制項或 view 控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="1b9a7-119">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="1b9a7-120">[GroupBy (格式之 ExpressionBinding 的 EnumerateCollection 元素) ](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)GroupBy (格式之 ExpressionBinding 的 EnumerateCollection 元素) </span><span class="sxs-lookup"><span data-stu-id="1b9a7-120">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="1b9a7-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="1b9a7-121">Optional element.</span></span><br /><br /> <span data-ttu-id="1b9a7-122">指定會顯示集合的元素。</span><span class="sxs-lookup"><span data-stu-id="1b9a7-122">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="1b9a7-123">GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1b9a7-123">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="1b9a7-124">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="1b9a7-124">Optional element.</span></span><br /><br /> <span data-ttu-id="1b9a7-125">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="1b9a7-125">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="1b9a7-126">GroupBy 之 ExpressionBinding 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1b9a7-126">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="1b9a7-127">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="1b9a7-127">Optional element.</span></span><br /><br /> <span data-ttu-id="1b9a7-128">指定控制項顯示其值的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="1b9a7-128">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="1b9a7-129">GroupBy 之 ExpressionBinding 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1b9a7-129">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="1b9a7-130">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="1b9a7-130">Optional element.</span></span><br /><br /> <span data-ttu-id="1b9a7-131">指定控制項顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="1b9a7-131">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1b9a7-132">父項目</span><span class="sxs-lookup"><span data-stu-id="1b9a7-132">Parent Elements</span></span>

|<span data-ttu-id="1b9a7-133">元素</span><span class="sxs-lookup"><span data-stu-id="1b9a7-133">Element</span></span>|<span data-ttu-id="1b9a7-134">描述</span><span class="sxs-lookup"><span data-stu-id="1b9a7-134">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1b9a7-135">GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1b9a7-135">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="1b9a7-136">定義自訂控制項視圖所顯示的資料，以及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="1b9a7-136">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="1b9a7-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b9a7-137">See Also</span></span>

[<span data-ttu-id="1b9a7-138">GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1b9a7-138">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="1b9a7-139">GroupBy 之 ExpressionBinding 的 EnumerateCollection 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1b9a7-139">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="1b9a7-140">GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1b9a7-140">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="1b9a7-141">GroupBy 之 ExpressionBinding 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1b9a7-141">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="1b9a7-142">GroupBy 之 ExpressionBinding 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1b9a7-142">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="1b9a7-143">GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1b9a7-143">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="1b9a7-144">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="1b9a7-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
