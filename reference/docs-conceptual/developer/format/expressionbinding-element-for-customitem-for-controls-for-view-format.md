---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)
description: 檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)
ms.openlocfilehash: da87bb26d21dcb051871e67997cc3fba7ce73c74
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649885"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="e35f0-103">檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e35f0-103">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="e35f0-104">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="e35f0-104">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="e35f0-105">當定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="e35f0-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e35f0-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式) 控制項專案 (格式) CustomEntries 專案的視圖控制項的控制項 (格式若為 CustomControl for View (格式) CustomEntry 元素，用於 CustomEntries 的控制項 (格式) CustomItem 專案的 CustomEntry 控制項的 ExpressionBinding， () 格式的控制項 CustomItem 的控制項 (的元素) </span><span class="sxs-lookup"><span data-stu-id="e35f0-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e35f0-107">語法</span><span class="sxs-lookup"><span data-stu-id="e35f0-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="e35f0-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e35f0-108">Attributes and Elements</span></span>

<span data-ttu-id="e35f0-109">下列各節說明屬性、子專案和元素的父元素 `ExpressionBinding` 。</span><span class="sxs-lookup"><span data-stu-id="e35f0-109">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e35f0-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e35f0-110">Attributes</span></span>

<span data-ttu-id="e35f0-111">無。</span><span class="sxs-lookup"><span data-stu-id="e35f0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e35f0-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e35f0-112">Child Elements</span></span>

|<span data-ttu-id="e35f0-113">元素</span><span class="sxs-lookup"><span data-stu-id="e35f0-113">Element</span></span>|<span data-ttu-id="e35f0-114">描述</span><span class="sxs-lookup"><span data-stu-id="e35f0-114">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="e35f0-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e35f0-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e35f0-116">定義這個控制項所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="e35f0-116">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="e35f0-117">檢視之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e35f0-117">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="e35f0-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e35f0-118">Optional element.</span></span><br /><br /> <span data-ttu-id="e35f0-119">指定通用控制項或 view 控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="e35f0-119">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="e35f0-120">檢視之控制項的 ExpressionBinding 的 EnumerateCollection 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e35f0-120">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="e35f0-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e35f0-121">Optional element.</span></span><br /><br /> <span data-ttu-id="e35f0-122">指定要顯示集合的元素。</span><span class="sxs-lookup"><span data-stu-id="e35f0-122">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="e35f0-123">View (Format) 的控制項之 ExpressionBinding 元素 ItemSelectionCondition </span><span class="sxs-lookup"><span data-stu-id="e35f0-123">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="e35f0-124">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e35f0-124">Optional element.</span></span><br /><br /> <span data-ttu-id="e35f0-125">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="e35f0-125">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="e35f0-126">檢視之控制項的 ExpressionBinding 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e35f0-126">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="e35f0-127">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e35f0-127">Optional element.</span></span><br /><br /> <span data-ttu-id="e35f0-128">指定控制項顯示其值的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="e35f0-128">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="e35f0-129">檢視之控制項的 ExpressionBinding 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e35f0-129">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="e35f0-130">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e35f0-130">Optional element.</span></span><br /><br /> <span data-ttu-id="e35f0-131">指定控制項顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="e35f0-131">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e35f0-132">父項目</span><span class="sxs-lookup"><span data-stu-id="e35f0-132">Parent Elements</span></span>

|<span data-ttu-id="e35f0-133">元素</span><span class="sxs-lookup"><span data-stu-id="e35f0-133">Element</span></span>|<span data-ttu-id="e35f0-134">描述</span><span class="sxs-lookup"><span data-stu-id="e35f0-134">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e35f0-135">檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e35f0-135">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="e35f0-136">定義控制項顯示的資料以及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="e35f0-136">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e35f0-137">備註</span><span class="sxs-lookup"><span data-stu-id="e35f0-137">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="e35f0-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e35f0-138">See Also</span></span>

[<span data-ttu-id="e35f0-139">檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e35f0-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="e35f0-140">檢視之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e35f0-140">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="e35f0-141">檢視之控制項的 ExpressionBinding 的 EnumerateCollection 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e35f0-141">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="e35f0-142">View (Format) 的控制項之 ExpressionBinding 元素 ItemSelectionCondition </span><span class="sxs-lookup"><span data-stu-id="e35f0-142">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="e35f0-143">檢視之控制項的 ExpressionBinding 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e35f0-143">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="e35f0-144">檢視之控制項的 ExpressionBinding 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e35f0-144">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="e35f0-145">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="e35f0-145">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
