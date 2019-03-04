---
title: ItemSelectionCondition CustomControl （格式） 的 ExpressionBinding 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858184"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="76d89-102">CustomControl 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="76d89-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="76d89-103">定義要使用這個控制項必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="76d89-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="76d89-104">沒有任何限制，選擇條件，您可以指定的控制項項目數目。</span><span class="sxs-lookup"><span data-stu-id="76d89-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="76d89-105">定義自訂控制項的檢視時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="76d89-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="76d89-106">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目 （格式） CustomEntries 項目 CustomControl CustomEntries 用於檢視 （格式） CustomItem 元素的檢視 （格式） CustomEntry 元素CustomEntry CustomControl CustomControl 的檢視 （格式） 的運算式繫結的檢視 （格式） ItemSelectionCondition 項目的的 CustomItem 的檢視 （格式） ExpressionBinding 元素</span><span class="sxs-lookup"><span data-stu-id="76d89-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="76d89-107">語法</span><span class="sxs-lookup"><span data-stu-id="76d89-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="76d89-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="76d89-108">Attributes and Elements</span></span>

<span data-ttu-id="76d89-109">下列各節說明屬性、 子項目和父項目`ItemSelectionCondition`項目。</span><span class="sxs-lookup"><span data-stu-id="76d89-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="76d89-110">屬性</span><span class="sxs-lookup"><span data-stu-id="76d89-110">Attributes</span></span>

<span data-ttu-id="76d89-111">無。</span><span class="sxs-lookup"><span data-stu-id="76d89-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="76d89-112">子元素</span><span class="sxs-lookup"><span data-stu-id="76d89-112">Child Elements</span></span>

|<span data-ttu-id="76d89-113">元素</span><span class="sxs-lookup"><span data-stu-id="76d89-113">Element</span></span>|<span data-ttu-id="76d89-114">描述</span><span class="sxs-lookup"><span data-stu-id="76d89-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="76d89-115">PropertyName ItemSelectionCondition CustomControl 檢視 （格式為的項目</span><span class="sxs-lookup"><span data-stu-id="76d89-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="76d89-116">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="76d89-116">Optional element.</span></span><br /><br /> <span data-ttu-id="76d89-117">指定觸發條件的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="76d89-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="76d89-118">ItemSelectionCondition CustomControl 檢視 （格式） 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="76d89-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="76d89-119">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="76d89-119">Optional element.</span></span><br /><br /> <span data-ttu-id="76d89-120">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="76d89-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="76d89-121">父元素</span><span class="sxs-lookup"><span data-stu-id="76d89-121">Parent Elements</span></span>

|<span data-ttu-id="76d89-122">元素</span><span class="sxs-lookup"><span data-stu-id="76d89-122">Element</span></span>|<span data-ttu-id="76d89-123">描述</span><span class="sxs-lookup"><span data-stu-id="76d89-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="76d89-124">ExpressionBinding CustomItem 如 CustomControl 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="76d89-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="76d89-125">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="76d89-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="76d89-126">備註</span><span class="sxs-lookup"><span data-stu-id="76d89-126">Remarks</span></span>

<span data-ttu-id="76d89-127">您可以指定一個屬性名稱或用於這種狀況的指令碼，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="76d89-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="76d89-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76d89-128">See Also</span></span>

[<span data-ttu-id="76d89-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="76d89-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="76d89-130">ExpressionBinding CustomItem 如 CustomControl 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="76d89-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
