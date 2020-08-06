---
title: View (Format) 的控制項之 CustomItem 的 ExpressionBinding 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6760bf17be58411948ecb3437bf18bce40073954
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773805"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="923dc-102">檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="923dc-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="923dc-103">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="923dc-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="923dc-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="923dc-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="923dc-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 (格式) CustomEntries 專案的控制項的控制項 (的 CustomControl 元素針對 CustomControl for View (格式) 的 CustomEntries for 控制項的 CustomEntry 專案， (格式]) CustomItem 元素（針對 view (格式的控制項，CustomEntry 的 ExpressionBinding 元素）) </span><span class="sxs-lookup"><span data-stu-id="923dc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="923dc-106">語法</span><span class="sxs-lookup"><span data-stu-id="923dc-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="923dc-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="923dc-107">Attributes and Elements</span></span>

<span data-ttu-id="923dc-108">下列各節說明屬性、子專案和元素的父元素 `ExpressionBinding` 。</span><span class="sxs-lookup"><span data-stu-id="923dc-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="923dc-109">屬性</span><span class="sxs-lookup"><span data-stu-id="923dc-109">Attributes</span></span>

<span data-ttu-id="923dc-110">無。</span><span class="sxs-lookup"><span data-stu-id="923dc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="923dc-111">子元素</span><span class="sxs-lookup"><span data-stu-id="923dc-111">Child Elements</span></span>

|<span data-ttu-id="923dc-112">元素</span><span class="sxs-lookup"><span data-stu-id="923dc-112">Element</span></span>|<span data-ttu-id="923dc-113">描述</span><span class="sxs-lookup"><span data-stu-id="923dc-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="923dc-114">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="923dc-114">Optional element.</span></span><br /><br /> <span data-ttu-id="923dc-115">定義此控制項所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="923dc-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="923dc-116">檢視之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="923dc-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="923dc-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="923dc-117">Optional element.</span></span><br /><br /> <span data-ttu-id="923dc-118">指定通用控制項或 view 控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="923dc-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="923dc-119">檢視之控制項的 ExpressionBinding 的 EnumerateCollection 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="923dc-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="923dc-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="923dc-120">Optional element.</span></span><br /><br /> <span data-ttu-id="923dc-121">指定顯示集合的元素。</span><span class="sxs-lookup"><span data-stu-id="923dc-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="923dc-122">View (Format) 的控制項之 ExpressionBinding 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="923dc-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="923dc-123">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="923dc-123">Optional element.</span></span><br /><br /> <span data-ttu-id="923dc-124">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="923dc-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="923dc-125">檢視之控制項的 ExpressionBinding 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="923dc-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="923dc-126">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="923dc-126">Optional element.</span></span><br /><br /> <span data-ttu-id="923dc-127">指定控制項顯示其值的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="923dc-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="923dc-128">檢視之控制項的 ExpressionBinding 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="923dc-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="923dc-129">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="923dc-129">Optional element.</span></span><br /><br /> <span data-ttu-id="923dc-130">指定控制項顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="923dc-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="923dc-131">父項目</span><span class="sxs-lookup"><span data-stu-id="923dc-131">Parent Elements</span></span>

|<span data-ttu-id="923dc-132">元素</span><span class="sxs-lookup"><span data-stu-id="923dc-132">Element</span></span>|<span data-ttu-id="923dc-133">描述</span><span class="sxs-lookup"><span data-stu-id="923dc-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="923dc-134">檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="923dc-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="923dc-135">定義控制項所顯示的資料及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="923dc-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="923dc-136">備註</span><span class="sxs-lookup"><span data-stu-id="923dc-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="923dc-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="923dc-137">See Also</span></span>

[<span data-ttu-id="923dc-138">檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="923dc-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="923dc-139">檢視之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="923dc-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="923dc-140">檢視之控制項的 ExpressionBinding 的 EnumerateCollection 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="923dc-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="923dc-141">View (Format) 的控制項之 ExpressionBinding 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="923dc-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="923dc-142">檢視之控制項的 ExpressionBinding 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="923dc-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="923dc-143">檢視之控制項的 ExpressionBinding 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="923dc-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="923dc-144">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="923dc-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
