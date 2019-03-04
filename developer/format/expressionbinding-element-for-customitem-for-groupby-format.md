---
title: ExpressionBinding CustomItem 的 GroupBy （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854924"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="8bbab-102">GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8bbab-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="8bbab-103">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="8bbab-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="8bbab-104">定義新的群組物件的顯示方式時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="8bbab-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="8bbab-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素CustomControl CustomEntry CustomItem 的 GroupBy （格式） 的 GroupBy （格式） ExpressionBinding 元素的 GroupBy （格式） CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="8bbab-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8bbab-106">語法</span><span class="sxs-lookup"><span data-stu-id="8bbab-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="8bbab-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="8bbab-107">Attributes and Elements</span></span>

<span data-ttu-id="8bbab-108">下列各節說明屬性、 子項目和父項目`ExpressionBinding`項目。</span><span class="sxs-lookup"><span data-stu-id="8bbab-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8bbab-109">屬性</span><span class="sxs-lookup"><span data-stu-id="8bbab-109">Attributes</span></span>

<span data-ttu-id="8bbab-110">無。</span><span class="sxs-lookup"><span data-stu-id="8bbab-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8bbab-111">子元素</span><span class="sxs-lookup"><span data-stu-id="8bbab-111">Child Elements</span></span>

|<span data-ttu-id="8bbab-112">元素</span><span class="sxs-lookup"><span data-stu-id="8bbab-112">Element</span></span>|<span data-ttu-id="8bbab-113">描述</span><span class="sxs-lookup"><span data-stu-id="8bbab-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="8bbab-114">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="8bbab-114">Optional element.</span></span><br /><br /> <span data-ttu-id="8bbab-115">定義會使用這個控制項的控制項。</span><span class="sxs-lookup"><span data-stu-id="8bbab-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="8bbab-116">CustomControlName ExpressionBinding 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="8bbab-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="8bbab-117">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="8bbab-117">Optional element.</span></span><br /><br /> <span data-ttu-id="8bbab-118">指定通用控制項的檢視控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="8bbab-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="8bbab-119">[EnumerateCollection ExpressionBinding 的 GroupBy （格式） 的項目](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection ExpressionBinding 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="8bbab-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="8bbab-120">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="8bbab-120">Optional element.</span></span><br /><br /> <span data-ttu-id="8bbab-121">指定集合的項目會顯示。</span><span class="sxs-lookup"><span data-stu-id="8bbab-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="8bbab-122">ItemSelectionCondition ExpressionBinding 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="8bbab-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="8bbab-123">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="8bbab-123">Optional element.</span></span><br /><br /> <span data-ttu-id="8bbab-124">定義要使用這個控制項必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="8bbab-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="8bbab-125">PropertyName ExpressionBinding 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="8bbab-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="8bbab-126">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="8bbab-126">Optional element.</span></span><br /><br /> <span data-ttu-id="8bbab-127">指定其值控制項所顯示的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="8bbab-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="8bbab-128">ExpressionBinding 的 GroupBy （格式） 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="8bbab-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="8bbab-129">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="8bbab-129">Optional element.</span></span><br /><br /> <span data-ttu-id="8bbab-130">指定其值控制項所顯示的指令碼。</span><span class="sxs-lookup"><span data-stu-id="8bbab-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8bbab-131">父元素</span><span class="sxs-lookup"><span data-stu-id="8bbab-131">Parent Elements</span></span>

|<span data-ttu-id="8bbab-132">元素</span><span class="sxs-lookup"><span data-stu-id="8bbab-132">Element</span></span>|<span data-ttu-id="8bbab-133">描述</span><span class="sxs-lookup"><span data-stu-id="8bbab-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8bbab-134">GroupBy （格式） 的 CustomEntry CustomItem 項目</span><span class="sxs-lookup"><span data-stu-id="8bbab-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="8bbab-135">定義自訂的控制項檢視所顯示的資料和顯示方式。</span><span class="sxs-lookup"><span data-stu-id="8bbab-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="8bbab-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bbab-136">See Also</span></span>

[<span data-ttu-id="8bbab-137">CustomControlName ExpressionBinding 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="8bbab-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="8bbab-138">EnumerateCollection ExpressionBinding 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="8bbab-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="8bbab-139">ItemSelectionCondition ExpressionBinding 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="8bbab-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="8bbab-140">PropertyName ExpressionBinding 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="8bbab-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="8bbab-141">ExpressionBinding 的 GroupBy （格式） 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="8bbab-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="8bbab-142">GroupBy （格式） 的 CustomEntry CustomItem 項目</span><span class="sxs-lookup"><span data-stu-id="8bbab-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="8bbab-143">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="8bbab-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
