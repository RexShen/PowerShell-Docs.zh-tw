---
title: ExpressionBinding CustomItem 如 CustomControl 檢視 （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860684"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="aa99c-102">檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="aa99c-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="aa99c-103">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="aa99c-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="aa99c-104">定義自訂控制項的檢視時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="aa99c-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="aa99c-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目進行檢視 （格式） 的檢視 （如 CustomControl CustomEntries CustomEntry 元素 CustomControl 的檢視 （格式） CustomEntries 項目格式） 的檢視 （格式） ExpressionBinding 項目，如 CustomControl 檢視 （格式） 的 CustomItem CustomControl CustomEntry CustomItem 項目</span><span class="sxs-lookup"><span data-stu-id="aa99c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aa99c-106">語法</span><span class="sxs-lookup"><span data-stu-id="aa99c-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="aa99c-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="aa99c-107">Attributes and Elements</span></span>

<span data-ttu-id="aa99c-108">下列各節說明屬性、 子項目和父項目`ExpressionBinding`項目。</span><span class="sxs-lookup"><span data-stu-id="aa99c-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aa99c-109">屬性</span><span class="sxs-lookup"><span data-stu-id="aa99c-109">Attributes</span></span>

<span data-ttu-id="aa99c-110">無。</span><span class="sxs-lookup"><span data-stu-id="aa99c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aa99c-111">子元素</span><span class="sxs-lookup"><span data-stu-id="aa99c-111">Child Elements</span></span>

|<span data-ttu-id="aa99c-112">元素</span><span class="sxs-lookup"><span data-stu-id="aa99c-112">Element</span></span>|<span data-ttu-id="aa99c-113">描述</span><span class="sxs-lookup"><span data-stu-id="aa99c-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="aa99c-114">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="aa99c-114">Optional element.</span></span><br /><br /> <span data-ttu-id="aa99c-115">定義會使用這個控制項的控制項。</span><span class="sxs-lookup"><span data-stu-id="aa99c-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="aa99c-116">CustomControlName CustomControl 檢視 （格式） 的 ExpressionBinding 的項目</span><span class="sxs-lookup"><span data-stu-id="aa99c-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="aa99c-117">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="aa99c-117">Optional element.</span></span><br /><br /> <span data-ttu-id="aa99c-118">指定通用控制項的檢視控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="aa99c-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="aa99c-119">EnumerateCollection CustomControl 檢視 （格式） 的 ExpressionBinding 的項目</span><span class="sxs-lookup"><span data-stu-id="aa99c-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="aa99c-120">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="aa99c-120">Optional element.</span></span><br /><br /> <span data-ttu-id="aa99c-121">指定集合的項目會顯示。</span><span class="sxs-lookup"><span data-stu-id="aa99c-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="aa99c-122">ItemSelectionCondition CustomControl 檢視 （格式） 的 ExpressionBinding 的項目</span><span class="sxs-lookup"><span data-stu-id="aa99c-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="aa99c-123">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="aa99c-123">Optional element.</span></span><br /><br /> <span data-ttu-id="aa99c-124">定義要使用這個控制項必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="aa99c-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="aa99c-125">PropertyName CustomControl 檢視 （格式） 的 ExpressionBinding 的項目</span><span class="sxs-lookup"><span data-stu-id="aa99c-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="aa99c-126">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="aa99c-126">Optional element.</span></span><br /><br /> <span data-ttu-id="aa99c-127">指定其值控制項所顯示的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="aa99c-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="aa99c-128">ExpressionBinding CustomCustomControl 檢視 （格式） 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="aa99c-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="aa99c-129">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="aa99c-129">Optional element.</span></span><br /><br /> <span data-ttu-id="aa99c-130">指定其值控制項所顯示的指令碼。</span><span class="sxs-lookup"><span data-stu-id="aa99c-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="aa99c-131">父元素</span><span class="sxs-lookup"><span data-stu-id="aa99c-131">Parent Elements</span></span>

|<span data-ttu-id="aa99c-132">元素</span><span class="sxs-lookup"><span data-stu-id="aa99c-132">Element</span></span>|<span data-ttu-id="aa99c-133">描述</span><span class="sxs-lookup"><span data-stu-id="aa99c-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aa99c-134">CustomControl 檢視 （格式） 的 CustomEntry CustomItem 項目</span><span class="sxs-lookup"><span data-stu-id="aa99c-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="aa99c-135">定義自訂的控制項檢視所顯示的資料和顯示方式。</span><span class="sxs-lookup"><span data-stu-id="aa99c-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="aa99c-136">備註</span><span class="sxs-lookup"><span data-stu-id="aa99c-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="aa99c-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa99c-137">See Also</span></span>

[<span data-ttu-id="aa99c-138">CustomControlName CustomControl 檢視 （格式） 的 ExpressionBinding 的項目</span><span class="sxs-lookup"><span data-stu-id="aa99c-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="aa99c-139">EnumerateCollection CustomControl 檢視 （格式） 的 ExpressionBinding 的項目</span><span class="sxs-lookup"><span data-stu-id="aa99c-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="aa99c-140">ItemSelectionCondition CustomControl 檢視 （格式） 的 ExpressionBinding 的項目</span><span class="sxs-lookup"><span data-stu-id="aa99c-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="aa99c-141">PropertyName CustomControl 檢視 （格式） 的 ExpressionBinding 的項目</span><span class="sxs-lookup"><span data-stu-id="aa99c-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="aa99c-142">ExpressionBinding CustomControl 檢視 （格式） 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="aa99c-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="aa99c-143">CustomControl 檢視 （格式） 的 CustomEntry CustomItem 項目</span><span class="sxs-lookup"><span data-stu-id="aa99c-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="aa99c-144">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="aa99c-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
