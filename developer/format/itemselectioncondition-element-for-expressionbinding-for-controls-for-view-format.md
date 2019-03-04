---
title: 用於檢視 （格式） 的控制項 ExpressionBinding ItemSelectionCondition 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861844"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="027ab-102">檢視之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="027ab-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="027ab-103">定義要使用這個控制項必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="027ab-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="027ab-104">定義可供檢視的控制項時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="027ab-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="027ab-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目CustomControl CustomEntries CustomEntry CustomItem 用於檢視 （格式） 的控制項的檢視 （格式） ExpressionBinding 元素的控制項的檢視 （格式） CustomItem 元素的控制項的檢視 （格式） CustomEntry 元素用於檢視 （格式） 的控制項 ExpressionBinding ItemSelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="027ab-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="027ab-106">語法</span><span class="sxs-lookup"><span data-stu-id="027ab-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="027ab-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="027ab-107">Attributes and Elements</span></span>

<span data-ttu-id="027ab-108">下列各節說明屬性、 子項目和父項目`ItemSelectionCondition`項目。</span><span class="sxs-lookup"><span data-stu-id="027ab-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="027ab-109">屬性</span><span class="sxs-lookup"><span data-stu-id="027ab-109">Attributes</span></span>

<span data-ttu-id="027ab-110">無。</span><span class="sxs-lookup"><span data-stu-id="027ab-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="027ab-111">子元素</span><span class="sxs-lookup"><span data-stu-id="027ab-111">Child Elements</span></span>

|<span data-ttu-id="027ab-112">元素</span><span class="sxs-lookup"><span data-stu-id="027ab-112">Element</span></span>|<span data-ttu-id="027ab-113">描述</span><span class="sxs-lookup"><span data-stu-id="027ab-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="027ab-114">PropertyName ItemSelectionCondition 用於檢視 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="027ab-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="027ab-115">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="027ab-115">Optional element.</span></span><br /><br /> <span data-ttu-id="027ab-116">指定觸發條件的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="027ab-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="027ab-117">用於檢視 （格式） 的控制項 ItemSelectionCondition 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="027ab-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="027ab-118">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="027ab-118">Optional element.</span></span><br /><br /> <span data-ttu-id="027ab-119">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="027ab-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="027ab-120">父元素</span><span class="sxs-lookup"><span data-stu-id="027ab-120">Parent Elements</span></span>

|<span data-ttu-id="027ab-121">元素</span><span class="sxs-lookup"><span data-stu-id="027ab-121">Element</span></span>|<span data-ttu-id="027ab-122">描述</span><span class="sxs-lookup"><span data-stu-id="027ab-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="027ab-123">ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="027ab-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="027ab-124">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="027ab-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="027ab-125">備註</span><span class="sxs-lookup"><span data-stu-id="027ab-125">Remarks</span></span>

<span data-ttu-id="027ab-126">您可以指定一個屬性名稱或用於這種狀況的指令碼，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="027ab-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="027ab-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="027ab-127">See Also</span></span>

[<span data-ttu-id="027ab-128">PropertyName ItemSelectionCondition 用於檢視 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="027ab-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="027ab-129">用於檢視 （格式） 的控制項 ItemSelectionCondition 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="027ab-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="027ab-130">ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="027ab-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="027ab-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="027ab-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
