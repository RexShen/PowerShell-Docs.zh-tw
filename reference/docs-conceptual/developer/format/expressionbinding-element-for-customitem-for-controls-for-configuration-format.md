---
title: 設定之控制項的 CustomItem 的 ExpressionBinding 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363187"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="ee558-102">設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ee558-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="ee558-103">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="ee558-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="ee558-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="ee558-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="ee558-105">Configuration 元素（格式）控制設定（format） CustomControl 元素的設定（格式）控制項專案的設定專案（格式） CustomControl 設定的 CustomEntries 元素（格式）Format） CustomEntry 元素，用於 CustomControl 控制項的 CustomItem 元素，用於 CustomEntry 的 configuration ExpressionBinding 元素設定的 CustomItem 專案的控制項（格式）</span><span class="sxs-lookup"><span data-stu-id="ee558-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ee558-106">語法</span><span class="sxs-lookup"><span data-stu-id="ee558-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="ee558-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="ee558-107">Attributes and Elements</span></span>

<span data-ttu-id="ee558-108">下列各節說明屬性、子專案，以及 `ExpressionBinding` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="ee558-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ee558-109">屬性</span><span class="sxs-lookup"><span data-stu-id="ee558-109">Attributes</span></span>

<span data-ttu-id="ee558-110">無。</span><span class="sxs-lookup"><span data-stu-id="ee558-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ee558-111">子元素</span><span class="sxs-lookup"><span data-stu-id="ee558-111">Child Elements</span></span>

|<span data-ttu-id="ee558-112">元素</span><span class="sxs-lookup"><span data-stu-id="ee558-112">Element</span></span>|<span data-ttu-id="ee558-113">描述</span><span class="sxs-lookup"><span data-stu-id="ee558-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="ee558-114">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="ee558-114">Optional element.</span></span><br /><br /> <span data-ttu-id="ee558-115">定義此控制項所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="ee558-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="ee558-116">設定之控制項的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ee558-116">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="ee558-117">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="ee558-117">Optional element.</span></span><br /><br /> <span data-ttu-id="ee558-118">指定通用控制項或 view 控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="ee558-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="ee558-119">設定之控制項的 ExpressionBinding 的 EnumerateCollection 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ee558-119">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="ee558-120">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="ee558-120">Optional element.</span></span><br /><br /> <span data-ttu-id="ee558-121">指定控制項會顯示集合的元素。</span><span class="sxs-lookup"><span data-stu-id="ee558-121">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="ee558-122">設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ee558-122">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="ee558-123">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="ee558-123">Optional element.</span></span><br /><br /> <span data-ttu-id="ee558-124">定義必須存在的條件，才能使用此通用控制項。</span><span class="sxs-lookup"><span data-stu-id="ee558-124">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="ee558-125">設定之控制項的 ExpressionBinding 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ee558-125">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="ee558-126">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="ee558-126">Optional element.</span></span><br /><br /> <span data-ttu-id="ee558-127">指定由通用控制項顯示其值的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="ee558-127">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="ee558-128">設定之控制項的 ExpressionBinding 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ee558-128">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="ee558-129">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="ee558-129">Optional element.</span></span><br /><br /> <span data-ttu-id="ee558-130">指定由通用控制項顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="ee558-130">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ee558-131">父元素</span><span class="sxs-lookup"><span data-stu-id="ee558-131">Parent Elements</span></span>

|<span data-ttu-id="ee558-132">元素</span><span class="sxs-lookup"><span data-stu-id="ee558-132">Element</span></span>|<span data-ttu-id="ee558-133">描述</span><span class="sxs-lookup"><span data-stu-id="ee558-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ee558-134">設定之控制項的 CustomEntry 的 CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="ee558-134">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="ee558-135">定義自訂控制項視圖顯示的資料，以及顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="ee558-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ee558-136">備註</span><span class="sxs-lookup"><span data-stu-id="ee558-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="ee558-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee558-137">See Also</span></span>

[<span data-ttu-id="ee558-138">設定之控制項的 CustomEntry 的 CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="ee558-138">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="ee558-139">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="ee558-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
