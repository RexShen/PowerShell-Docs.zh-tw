---
title: GroupBy 之 CustomItem 的 ExpressionBinding 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368627"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="79fd8-102">GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="79fd8-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="79fd8-103">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="79fd8-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="79fd8-104">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="79fd8-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="79fd8-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（format） CustomEntries 專案的 groupby （format） CustomControl 元素，適用于的 CustomControl for GroupBy （format） CustomEntry 元素適用于 CustomEntry for groupby （format） ExpressionBinding 元素的 GroupBy （format） CustomItem 元素的 CustomControl</span><span class="sxs-lookup"><span data-stu-id="79fd8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="79fd8-106">語法</span><span class="sxs-lookup"><span data-stu-id="79fd8-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="79fd8-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="79fd8-107">Attributes and Elements</span></span>

<span data-ttu-id="79fd8-108">下列各節說明屬性、子專案，以及 `ExpressionBinding` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="79fd8-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="79fd8-109">屬性</span><span class="sxs-lookup"><span data-stu-id="79fd8-109">Attributes</span></span>

<span data-ttu-id="79fd8-110">無。</span><span class="sxs-lookup"><span data-stu-id="79fd8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="79fd8-111">子元素</span><span class="sxs-lookup"><span data-stu-id="79fd8-111">Child Elements</span></span>

|<span data-ttu-id="79fd8-112">元素</span><span class="sxs-lookup"><span data-stu-id="79fd8-112">Element</span></span>|<span data-ttu-id="79fd8-113">描述</span><span class="sxs-lookup"><span data-stu-id="79fd8-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="79fd8-114">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="79fd8-114">Optional element.</span></span><br /><br /> <span data-ttu-id="79fd8-115">定義此控制項所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="79fd8-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="79fd8-116">GroupBy 之 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="79fd8-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="79fd8-117">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="79fd8-117">Optional element.</span></span><br /><br /> <span data-ttu-id="79fd8-118">指定通用控制項或 view 控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="79fd8-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="79fd8-119">[GroupBy 之 ExpressionBinding 的 EnumerateCollection 元素（格式）](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)GroupBy 之 ExpressionBinding 的 EnumerateCollection 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="79fd8-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="79fd8-120">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="79fd8-120">Optional element.</span></span><br /><br /> <span data-ttu-id="79fd8-121">指定會顯示集合的元素。</span><span class="sxs-lookup"><span data-stu-id="79fd8-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="79fd8-122">GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="79fd8-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="79fd8-123">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="79fd8-123">Optional element.</span></span><br /><br /> <span data-ttu-id="79fd8-124">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="79fd8-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="79fd8-125">GroupBy 之 ExpressionBinding 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="79fd8-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="79fd8-126">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="79fd8-126">Optional element.</span></span><br /><br /> <span data-ttu-id="79fd8-127">指定控制項顯示其值的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="79fd8-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="79fd8-128">GroupBy 的 ExpressionBinding 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="79fd8-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="79fd8-129">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="79fd8-129">Optional element.</span></span><br /><br /> <span data-ttu-id="79fd8-130">指定控制項顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="79fd8-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="79fd8-131">父元素</span><span class="sxs-lookup"><span data-stu-id="79fd8-131">Parent Elements</span></span>

|<span data-ttu-id="79fd8-132">元素</span><span class="sxs-lookup"><span data-stu-id="79fd8-132">Element</span></span>|<span data-ttu-id="79fd8-133">描述</span><span class="sxs-lookup"><span data-stu-id="79fd8-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="79fd8-134">GroupBy 之 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="79fd8-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="79fd8-135">定義自訂控制項視圖顯示的資料，以及顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="79fd8-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="79fd8-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79fd8-136">See Also</span></span>

[<span data-ttu-id="79fd8-137">GroupBy 之 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="79fd8-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="79fd8-138">GroupBy 之 ExpressionBinding 的 EnumerateCollection 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="79fd8-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="79fd8-139">GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="79fd8-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="79fd8-140">GroupBy 之 ExpressionBinding 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="79fd8-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="79fd8-141">GroupBy 的 ExpressionBinding 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="79fd8-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="79fd8-142">GroupBy 之 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="79fd8-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="79fd8-143">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="79fd8-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
