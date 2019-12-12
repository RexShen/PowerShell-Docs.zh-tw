---
title: View 之控制項的 CustomItem 的 ExpressionBinding 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363777"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="519ba-102">檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="519ba-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="519ba-103">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="519ba-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="519ba-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="519ba-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="519ba-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素CustomControl for View （format） CustomEntry 元素 for CustomEntries for view （format） CustomItem 元素 for view （format） CustomEntry 元素 for view （format） ExpressionBinding 的控制項</span><span class="sxs-lookup"><span data-stu-id="519ba-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="519ba-106">語法</span><span class="sxs-lookup"><span data-stu-id="519ba-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="519ba-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="519ba-107">Attributes and Elements</span></span>

<span data-ttu-id="519ba-108">下列各節說明屬性、子專案，以及 `ExpressionBinding` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="519ba-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="519ba-109">屬性</span><span class="sxs-lookup"><span data-stu-id="519ba-109">Attributes</span></span>

<span data-ttu-id="519ba-110">無。</span><span class="sxs-lookup"><span data-stu-id="519ba-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="519ba-111">子元素</span><span class="sxs-lookup"><span data-stu-id="519ba-111">Child Elements</span></span>

|<span data-ttu-id="519ba-112">元素</span><span class="sxs-lookup"><span data-stu-id="519ba-112">Element</span></span>|<span data-ttu-id="519ba-113">描述</span><span class="sxs-lookup"><span data-stu-id="519ba-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="519ba-114">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="519ba-114">Optional element.</span></span><br /><br /> <span data-ttu-id="519ba-115">定義此控制項所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="519ba-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="519ba-116">View 之控制項的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="519ba-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="519ba-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="519ba-117">Optional element.</span></span><br /><br /> <span data-ttu-id="519ba-118">指定通用控制項或 view 控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="519ba-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="519ba-119">View 之控制項的 ExpressionBinding 的 EnumerateCollection 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="519ba-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="519ba-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="519ba-120">Optional element.</span></span><br /><br /> <span data-ttu-id="519ba-121">指定顯示集合的元素。</span><span class="sxs-lookup"><span data-stu-id="519ba-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="519ba-122">View 之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="519ba-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="519ba-123">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="519ba-123">Optional element.</span></span><br /><br /> <span data-ttu-id="519ba-124">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="519ba-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="519ba-125">View 之控制項的 ExpressionBinding 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="519ba-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="519ba-126">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="519ba-126">Optional element.</span></span><br /><br /> <span data-ttu-id="519ba-127">指定控制項顯示其值的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="519ba-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="519ba-128">View 之控制項的 ExpressionBinding 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="519ba-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="519ba-129">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="519ba-129">Optional element.</span></span><br /><br /> <span data-ttu-id="519ba-130">指定控制項顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="519ba-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="519ba-131">父元素</span><span class="sxs-lookup"><span data-stu-id="519ba-131">Parent Elements</span></span>

|<span data-ttu-id="519ba-132">元素</span><span class="sxs-lookup"><span data-stu-id="519ba-132">Element</span></span>|<span data-ttu-id="519ba-133">描述</span><span class="sxs-lookup"><span data-stu-id="519ba-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="519ba-134">View 之控制項的 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="519ba-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="519ba-135">定義控制項所顯示的資料及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="519ba-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="519ba-136">備註</span><span class="sxs-lookup"><span data-stu-id="519ba-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="519ba-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="519ba-137">See Also</span></span>

[<span data-ttu-id="519ba-138">View 之控制項的 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="519ba-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="519ba-139">View 之控制項的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="519ba-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="519ba-140">View 之控制項的 ExpressionBinding 的 EnumerateCollection 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="519ba-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="519ba-141">View 之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="519ba-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="519ba-142">View 之控制項的 ExpressionBinding 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="519ba-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="519ba-143">View 之控制項的 ExpressionBinding 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="519ba-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="519ba-144">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="519ba-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
