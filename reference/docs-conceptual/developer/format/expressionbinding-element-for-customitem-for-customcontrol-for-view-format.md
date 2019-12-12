---
title: CustomControl for View 的 CustomItem 的 ExpressionBinding 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363147"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="689e5-102">檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="689e5-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="689e5-103">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="689e5-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="689e5-104">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="689e5-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="689e5-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素 for view （format） CustomEntries 元素 for CustomEntry for view （format） CustomEntries 元素Format） CustomItem 元素 for CustomControl for View （Format） ExpressionBinding 元素 for CustomItem for View （格式）</span><span class="sxs-lookup"><span data-stu-id="689e5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="689e5-106">語法</span><span class="sxs-lookup"><span data-stu-id="689e5-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="689e5-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="689e5-107">Attributes and Elements</span></span>

<span data-ttu-id="689e5-108">下列各節說明屬性、子專案，以及 `ExpressionBinding` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="689e5-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="689e5-109">屬性</span><span class="sxs-lookup"><span data-stu-id="689e5-109">Attributes</span></span>

<span data-ttu-id="689e5-110">無。</span><span class="sxs-lookup"><span data-stu-id="689e5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="689e5-111">子元素</span><span class="sxs-lookup"><span data-stu-id="689e5-111">Child Elements</span></span>

|<span data-ttu-id="689e5-112">元素</span><span class="sxs-lookup"><span data-stu-id="689e5-112">Element</span></span>|<span data-ttu-id="689e5-113">描述</span><span class="sxs-lookup"><span data-stu-id="689e5-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="689e5-114">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="689e5-114">Optional element.</span></span><br /><br /> <span data-ttu-id="689e5-115">定義此控制項所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="689e5-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="689e5-116">CustomControl for View 的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="689e5-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="689e5-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="689e5-117">Optional element.</span></span><br /><br /> <span data-ttu-id="689e5-118">指定通用控制項或 view 控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="689e5-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="689e5-119">CustomControl for View 的 ExpressionBinding 的 EnumerateCollection 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="689e5-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="689e5-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="689e5-120">Optional element.</span></span><br /><br /> <span data-ttu-id="689e5-121">指定會顯示集合的元素。</span><span class="sxs-lookup"><span data-stu-id="689e5-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="689e5-122">CustomControl for View 的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="689e5-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="689e5-123">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="689e5-123">Optional element.</span></span><br /><br /> <span data-ttu-id="689e5-124">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="689e5-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="689e5-125">ExpressionBinding for CustomControl for View 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="689e5-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="689e5-126">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="689e5-126">Optional element.</span></span><br /><br /> <span data-ttu-id="689e5-127">指定控制項顯示其值的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="689e5-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="689e5-128">ExpressionBinding for CustomCustomControl for View 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="689e5-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="689e5-129">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="689e5-129">Optional element.</span></span><br /><br /> <span data-ttu-id="689e5-130">指定控制項顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="689e5-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="689e5-131">父元素</span><span class="sxs-lookup"><span data-stu-id="689e5-131">Parent Elements</span></span>

|<span data-ttu-id="689e5-132">元素</span><span class="sxs-lookup"><span data-stu-id="689e5-132">Element</span></span>|<span data-ttu-id="689e5-133">描述</span><span class="sxs-lookup"><span data-stu-id="689e5-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="689e5-134">CustomControl for View 的 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="689e5-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="689e5-135">定義自訂控制項視圖顯示的資料，以及顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="689e5-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="689e5-136">備註</span><span class="sxs-lookup"><span data-stu-id="689e5-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="689e5-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="689e5-137">See Also</span></span>

[<span data-ttu-id="689e5-138">CustomControl for View 的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="689e5-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="689e5-139">CustomControl for View 的 ExpressionBinding 的 EnumerateCollection 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="689e5-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="689e5-140">CustomControl for View 的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="689e5-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="689e5-141">ExpressionBinding for CustomControl for View 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="689e5-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="689e5-142">ExpressionBinding for CustomControl for View 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="689e5-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="689e5-143">CustomControl for View 的 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="689e5-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="689e5-144">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="689e5-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
