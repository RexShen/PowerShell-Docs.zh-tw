---
title: ItemSelectionCondition ExpressionBinding 的 GroupBy （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853134"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="2fcc0-102">GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2fcc0-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="2fcc0-103">定義要使用這個控制項必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="2fcc0-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="2fcc0-104">沒有任何限制，選擇條件，您可以指定的控制項項目數目。</span><span class="sxs-lookup"><span data-stu-id="2fcc0-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="2fcc0-105">定義新的群組物件的顯示方式時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="2fcc0-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="2fcc0-106">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素CustomControl CustomEntry CustomItem ExpressionBinding 的 GroupBy （格式） 的 GroupBy （格式） ItemSelectionCondition 元素的 GroupBy （格式） ExpressionBinding 元素的 GroupBy （格式） CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="2fcc0-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2fcc0-107">語法</span><span class="sxs-lookup"><span data-stu-id="2fcc0-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2fcc0-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="2fcc0-108">Attributes and Elements</span></span>

<span data-ttu-id="2fcc0-109">下列各節說明屬性、 子項目和父項目`ItemSelectionCondition`項目。</span><span class="sxs-lookup"><span data-stu-id="2fcc0-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2fcc0-110">屬性</span><span class="sxs-lookup"><span data-stu-id="2fcc0-110">Attributes</span></span>

<span data-ttu-id="2fcc0-111">無。</span><span class="sxs-lookup"><span data-stu-id="2fcc0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2fcc0-112">子元素</span><span class="sxs-lookup"><span data-stu-id="2fcc0-112">Child Elements</span></span>

|<span data-ttu-id="2fcc0-113">元素</span><span class="sxs-lookup"><span data-stu-id="2fcc0-113">Element</span></span>|<span data-ttu-id="2fcc0-114">描述</span><span class="sxs-lookup"><span data-stu-id="2fcc0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2fcc0-115">PropertyName ItemSelectionCondition 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="2fcc0-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="2fcc0-116">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="2fcc0-116">Optional element.</span></span><br /><br /> <span data-ttu-id="2fcc0-117">指定觸發條件的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="2fcc0-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="2fcc0-118">GroupBy （格式） 的 ItemSelectionCondition 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="2fcc0-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="2fcc0-119">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="2fcc0-119">Optional element.</span></span><br /><br /> <span data-ttu-id="2fcc0-120">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="2fcc0-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2fcc0-121">父元素</span><span class="sxs-lookup"><span data-stu-id="2fcc0-121">Parent Elements</span></span>

|<span data-ttu-id="2fcc0-122">元素</span><span class="sxs-lookup"><span data-stu-id="2fcc0-122">Element</span></span>|<span data-ttu-id="2fcc0-123">描述</span><span class="sxs-lookup"><span data-stu-id="2fcc0-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2fcc0-124">ExpressionBinding CustomItem 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="2fcc0-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="2fcc0-125">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="2fcc0-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2fcc0-126">備註</span><span class="sxs-lookup"><span data-stu-id="2fcc0-126">Remarks</span></span>

<span data-ttu-id="2fcc0-127">您可以指定一個屬性名稱或用於這種狀況的指令碼，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="2fcc0-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="2fcc0-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2fcc0-128">See Also</span></span>

[<span data-ttu-id="2fcc0-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="2fcc0-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="2fcc0-130">ExpressionBinding CustomItem 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="2fcc0-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
