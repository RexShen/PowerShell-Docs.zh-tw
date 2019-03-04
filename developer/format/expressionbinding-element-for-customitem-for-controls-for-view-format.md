---
title: ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858294"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="14db8-102">檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="14db8-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="14db8-103">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="14db8-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="14db8-104">定義可供檢視的控制項時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="14db8-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="14db8-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目CustomControl CustomEntries CustomEntry CustomItem 用於檢視 （格式） 的控制項的檢視 （格式） ExpressionBinding 元素的控制項的檢視 （格式） CustomItem 元素的控制項的檢視 （格式） CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="14db8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="14db8-106">語法</span><span class="sxs-lookup"><span data-stu-id="14db8-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="14db8-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="14db8-107">Attributes and Elements</span></span>

<span data-ttu-id="14db8-108">下列各節說明屬性、 子項目和父項目`ExpressionBinding`項目。</span><span class="sxs-lookup"><span data-stu-id="14db8-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="14db8-109">屬性</span><span class="sxs-lookup"><span data-stu-id="14db8-109">Attributes</span></span>

<span data-ttu-id="14db8-110">無。</span><span class="sxs-lookup"><span data-stu-id="14db8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="14db8-111">子元素</span><span class="sxs-lookup"><span data-stu-id="14db8-111">Child Elements</span></span>

|<span data-ttu-id="14db8-112">元素</span><span class="sxs-lookup"><span data-stu-id="14db8-112">Element</span></span>|<span data-ttu-id="14db8-113">描述</span><span class="sxs-lookup"><span data-stu-id="14db8-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="14db8-114">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="14db8-114">Optional element.</span></span><br /><br /> <span data-ttu-id="14db8-115">定義會使用這個控制項的控制項。</span><span class="sxs-lookup"><span data-stu-id="14db8-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="14db8-116">用於檢視 （格式） 的控制項 ExpressionBinding CustomControlName 項目</span><span class="sxs-lookup"><span data-stu-id="14db8-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="14db8-117">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="14db8-117">Optional element.</span></span><br /><br /> <span data-ttu-id="14db8-118">指定通用控制項的檢視控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="14db8-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="14db8-119">用於檢視 （格式） 的控制項 ExpressionBinding EnumerateCollection 項目</span><span class="sxs-lookup"><span data-stu-id="14db8-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="14db8-120">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="14db8-120">Optional element.</span></span><br /><br /> <span data-ttu-id="14db8-121">指定要顯示集合的項目。</span><span class="sxs-lookup"><span data-stu-id="14db8-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="14db8-122">用於檢視 （格式） 的控制項 ExpressionBinding ItemSelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="14db8-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="14db8-123">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="14db8-123">Optional element.</span></span><br /><br /> <span data-ttu-id="14db8-124">定義要使用這個控制項必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="14db8-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="14db8-125">PropertyName ExpressionBinding 的控制項檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="14db8-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="14db8-126">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="14db8-126">Optional element.</span></span><br /><br /> <span data-ttu-id="14db8-127">指定其值控制項所顯示的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="14db8-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="14db8-128">ExpressionBinding 的控制項檢視 （格式） 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="14db8-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="14db8-129">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="14db8-129">Optional element.</span></span><br /><br /> <span data-ttu-id="14db8-130">指定其值控制項所顯示的指令碼。</span><span class="sxs-lookup"><span data-stu-id="14db8-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="14db8-131">父元素</span><span class="sxs-lookup"><span data-stu-id="14db8-131">Parent Elements</span></span>

|<span data-ttu-id="14db8-132">元素</span><span class="sxs-lookup"><span data-stu-id="14db8-132">Element</span></span>|<span data-ttu-id="14db8-133">描述</span><span class="sxs-lookup"><span data-stu-id="14db8-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="14db8-134">用於檢視 （格式） 的控制項 CustomEntry CustomItem 項目</span><span class="sxs-lookup"><span data-stu-id="14db8-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="14db8-135">定義控制項所顯示的資料和顯示方式。</span><span class="sxs-lookup"><span data-stu-id="14db8-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="14db8-136">備註</span><span class="sxs-lookup"><span data-stu-id="14db8-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="14db8-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14db8-137">See Also</span></span>

[<span data-ttu-id="14db8-138">用於檢視 （格式） 的控制項 CustomEntry CustomItem 項目</span><span class="sxs-lookup"><span data-stu-id="14db8-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="14db8-139">用於檢視 （格式） 的控制項 ExpressionBinding CustomControlName 項目</span><span class="sxs-lookup"><span data-stu-id="14db8-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="14db8-140">用於檢視 （格式） 的控制項 ExpressionBinding EnumerateCollection 項目</span><span class="sxs-lookup"><span data-stu-id="14db8-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="14db8-141">用於檢視 （格式） 的控制項 ExpressionBinding ItemSelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="14db8-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="14db8-142">PropertyName ExpressionBinding 的控制項檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="14db8-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="14db8-143">ExpressionBinding 的控制項檢視 （格式） 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="14db8-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="14db8-144">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="14db8-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
