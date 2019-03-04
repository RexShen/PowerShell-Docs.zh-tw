---
title: ExpressionBinding CustomItem 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855134"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="e3194-102">設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e3194-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e3194-103">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="e3194-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="e3194-104">定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="e3194-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e3194-105">組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目CustomControl CustomEntry CustomItem 組態 （格式） 的控制項設定 ExpressionBinding 元素的控制項的組態 （格式） CustomItem 元素的控制項的格式） CustomEntry 項目</span><span class="sxs-lookup"><span data-stu-id="e3194-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e3194-106">語法</span><span class="sxs-lookup"><span data-stu-id="e3194-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="e3194-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="e3194-107">Attributes and Elements</span></span>

<span data-ttu-id="e3194-108">下列各節說明屬性、 子項目和父項目`ExpressionBinding`項目。</span><span class="sxs-lookup"><span data-stu-id="e3194-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e3194-109">屬性</span><span class="sxs-lookup"><span data-stu-id="e3194-109">Attributes</span></span>

<span data-ttu-id="e3194-110">無。</span><span class="sxs-lookup"><span data-stu-id="e3194-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e3194-111">子元素</span><span class="sxs-lookup"><span data-stu-id="e3194-111">Child Elements</span></span>

|<span data-ttu-id="e3194-112">元素</span><span class="sxs-lookup"><span data-stu-id="e3194-112">Element</span></span>|<span data-ttu-id="e3194-113">描述</span><span class="sxs-lookup"><span data-stu-id="e3194-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="e3194-114">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="e3194-114">Optional element.</span></span><br /><br /> <span data-ttu-id="e3194-115">定義會使用這個控制項的控制項。</span><span class="sxs-lookup"><span data-stu-id="e3194-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="e3194-116">CustomControlName ExpressionBinding 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="e3194-116">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e3194-117">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="e3194-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e3194-118">指定通用控制項的檢視控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="e3194-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="e3194-119">EnumerateCollection ExpressionBinding 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="e3194-119">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e3194-120">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="e3194-120">Optional element.</span></span><br /><br /> <span data-ttu-id="e3194-121">指定集合的項目會顯示控制項。</span><span class="sxs-lookup"><span data-stu-id="e3194-121">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="e3194-122">ItemSelectionCondition ExpressionBinding 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="e3194-122">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e3194-123">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="e3194-123">Optional element.</span></span><br /><br /> <span data-ttu-id="e3194-124">定義要使用這個通用控制項必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="e3194-124">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="e3194-125">PropertyName ExpressionBinding 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="e3194-125">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e3194-126">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="e3194-126">Optional element.</span></span><br /><br /> <span data-ttu-id="e3194-127">指定其值會顯示通用控制項的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="e3194-127">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="e3194-128">ExpressionBinding 組態 （格式） 的控制項的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="e3194-128">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e3194-129">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="e3194-129">Optional element.</span></span><br /><br /> <span data-ttu-id="e3194-130">指定其值常見的控制項所顯示的指令碼。</span><span class="sxs-lookup"><span data-stu-id="e3194-130">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e3194-131">父元素</span><span class="sxs-lookup"><span data-stu-id="e3194-131">Parent Elements</span></span>

|<span data-ttu-id="e3194-132">元素</span><span class="sxs-lookup"><span data-stu-id="e3194-132">Element</span></span>|<span data-ttu-id="e3194-133">描述</span><span class="sxs-lookup"><span data-stu-id="e3194-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3194-134">組態控制項 CustomEntry CustomItem 項目</span><span class="sxs-lookup"><span data-stu-id="e3194-134">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="e3194-135">定義自訂的控制項檢視所顯示的資料和顯示方式。</span><span class="sxs-lookup"><span data-stu-id="e3194-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e3194-136">備註</span><span class="sxs-lookup"><span data-stu-id="e3194-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="e3194-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3194-137">See Also</span></span>

[<span data-ttu-id="e3194-138">組態控制項 CustomEntry CustomItem 項目</span><span class="sxs-lookup"><span data-stu-id="e3194-138">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="e3194-139">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="e3194-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
