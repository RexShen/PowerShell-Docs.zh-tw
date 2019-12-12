---
title: CustomControl 之 ExpressionBinding 的 ItemSelectionCondition 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362907"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="f2b02-102">CustomControl 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="f2b02-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="f2b02-103">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="f2b02-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="f2b02-104">可以針對控制項專案指定的選取條件數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="f2b02-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="f2b02-105">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="f2b02-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="f2b02-106">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素（format） CustomEntries 元素，用於 CustomEntry for View （Format） CustomEntries 元素的 CustomControl for view （format） CustomItem 元素CustomEntry for view （Format） ExpressionBinding 元素 for CustomControl for view （Format） ItemSelectionCondition 元素用於 CustomControl for View 的運算式系結（格式）</span><span class="sxs-lookup"><span data-stu-id="f2b02-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f2b02-107">語法</span><span class="sxs-lookup"><span data-stu-id="f2b02-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f2b02-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="f2b02-108">Attributes and Elements</span></span>

<span data-ttu-id="f2b02-109">下列各節說明屬性、子專案，以及 `ItemSelectionCondition` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="f2b02-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f2b02-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f2b02-110">Attributes</span></span>

<span data-ttu-id="f2b02-111">無。</span><span class="sxs-lookup"><span data-stu-id="f2b02-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f2b02-112">子元素</span><span class="sxs-lookup"><span data-stu-id="f2b02-112">Child Elements</span></span>

|<span data-ttu-id="f2b02-113">元素</span><span class="sxs-lookup"><span data-stu-id="f2b02-113">Element</span></span>|<span data-ttu-id="f2b02-114">描述</span><span class="sxs-lookup"><span data-stu-id="f2b02-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2b02-115">ItemSelectionCondition for CustomControl for View 的 PropertyName 元素（格式</span><span class="sxs-lookup"><span data-stu-id="f2b02-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="f2b02-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f2b02-116">Optional element.</span></span><br /><br /> <span data-ttu-id="f2b02-117">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="f2b02-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f2b02-118">ItemSelectionCondition for CustomControl for View 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f2b02-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="f2b02-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f2b02-119">Optional element.</span></span><br /><br /> <span data-ttu-id="f2b02-120">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="f2b02-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f2b02-121">父元素</span><span class="sxs-lookup"><span data-stu-id="f2b02-121">Parent Elements</span></span>

|<span data-ttu-id="f2b02-122">元素</span><span class="sxs-lookup"><span data-stu-id="f2b02-122">Element</span></span>|<span data-ttu-id="f2b02-123">描述</span><span class="sxs-lookup"><span data-stu-id="f2b02-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2b02-124">CustomControl for View 的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f2b02-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="f2b02-125">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="f2b02-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f2b02-126">備註</span><span class="sxs-lookup"><span data-stu-id="f2b02-126">Remarks</span></span>

<span data-ttu-id="f2b02-127">您可以為此條件指定一個屬性名稱或腳本，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="f2b02-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2b02-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2b02-128">See Also</span></span>

[<span data-ttu-id="f2b02-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="f2b02-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="f2b02-130">CustomControl for View 的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f2b02-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
