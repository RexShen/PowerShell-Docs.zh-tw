---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)
description: 檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)
ms.openlocfilehash: 8f4bfef4f6c65c6dabc7a776dda1083bac11fdf7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648188"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="b2984-103">檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b2984-103">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="b2984-104">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="b2984-104">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="b2984-105">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="b2984-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="b2984-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) CustomEntries 元素 for View (format) CustomEntry for CustomEntries for CustomControl for view (format) CustomItem 專案 for CustomEntry for CustomControl for view (format) ExpressionBinding 專案 for CustomItem for CustomControl for view (格式) </span><span class="sxs-lookup"><span data-stu-id="b2984-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b2984-107">語法</span><span class="sxs-lookup"><span data-stu-id="b2984-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="b2984-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b2984-108">Attributes and Elements</span></span>

<span data-ttu-id="b2984-109">下列各節說明屬性、子專案和元素的父元素 `ExpressionBinding` 。</span><span class="sxs-lookup"><span data-stu-id="b2984-109">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b2984-110">屬性</span><span class="sxs-lookup"><span data-stu-id="b2984-110">Attributes</span></span>

<span data-ttu-id="b2984-111">無。</span><span class="sxs-lookup"><span data-stu-id="b2984-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b2984-112">子元素</span><span class="sxs-lookup"><span data-stu-id="b2984-112">Child Elements</span></span>

|<span data-ttu-id="b2984-113">元素</span><span class="sxs-lookup"><span data-stu-id="b2984-113">Element</span></span>|<span data-ttu-id="b2984-114">描述</span><span class="sxs-lookup"><span data-stu-id="b2984-114">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="b2984-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="b2984-115">Optional element.</span></span><br /><br /> <span data-ttu-id="b2984-116">定義這個控制項所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="b2984-116">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="b2984-117">檢視之 CustomControl 的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b2984-117">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="b2984-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="b2984-118">Optional element.</span></span><br /><br /> <span data-ttu-id="b2984-119">指定通用控制項或 view 控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="b2984-119">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="b2984-120">檢視之 CustomControl 的 ExpressionBinding 的 EnumerateCollection 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b2984-120">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="b2984-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="b2984-121">Optional element.</span></span><br /><br /> <span data-ttu-id="b2984-122">指定會顯示集合的元素。</span><span class="sxs-lookup"><span data-stu-id="b2984-122">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="b2984-123">適用于 CustomControl 的 ExpressionBinding ItemSelectionCondition 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="b2984-123">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="b2984-124">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="b2984-124">Optional element.</span></span><br /><br /> <span data-ttu-id="b2984-125">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="b2984-125">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="b2984-126">檢視之 CustomControl 的 ExpressionBinding 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b2984-126">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="b2984-127">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="b2984-127">Optional element.</span></span><br /><br /> <span data-ttu-id="b2984-128">指定控制項顯示其值的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="b2984-128">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="b2984-129">ExpressionBinding for CustomCustomControl for View (格式的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="b2984-129">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="b2984-130">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="b2984-130">Optional element.</span></span><br /><br /> <span data-ttu-id="b2984-131">指定控制項顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="b2984-131">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b2984-132">父項目</span><span class="sxs-lookup"><span data-stu-id="b2984-132">Parent Elements</span></span>

|<span data-ttu-id="b2984-133">元素</span><span class="sxs-lookup"><span data-stu-id="b2984-133">Element</span></span>|<span data-ttu-id="b2984-134">描述</span><span class="sxs-lookup"><span data-stu-id="b2984-134">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b2984-135">檢視之 CustomControl 的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b2984-135">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="b2984-136">定義自訂控制項視圖所顯示的資料，以及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="b2984-136">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b2984-137">備註</span><span class="sxs-lookup"><span data-stu-id="b2984-137">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="b2984-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2984-138">See Also</span></span>

[<span data-ttu-id="b2984-139">檢視之 CustomControl 的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b2984-139">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b2984-140">檢視之 CustomControl 的 ExpressionBinding 的 EnumerateCollection 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b2984-140">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b2984-141">適用于 CustomControl 的 ExpressionBinding ItemSelectionCondition 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="b2984-141">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="b2984-142">檢視之 CustomControl 的 ExpressionBinding 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b2984-142">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b2984-143">檢視之 CustomControl 的 ExpressionBinding 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b2984-143">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b2984-144">檢視之 CustomControl 的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b2984-144">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b2984-145">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="b2984-145">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
