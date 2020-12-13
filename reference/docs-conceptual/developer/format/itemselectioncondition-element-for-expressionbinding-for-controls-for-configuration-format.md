---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)
description: 設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)
ms.openlocfilehash: 6bd3d386ba64b33a1744fcc9e602cf13404765a0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648089"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="f8a8b-103">設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="f8a8b-103">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="f8a8b-104">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="f8a8b-104">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="f8a8b-105">當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="f8a8b-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="f8a8b-106">設定元素 (格式) 控制項的設定元素 (格式) 控制項的設定 (格式) CustomControl 元素，用於 CustomControl 的設定 (格式) CustomEntry 元素針對 configuration (格式的控制項的 CustomControl 格式) CustomItem 元素，用於 CustomEntry 的控制項，以設定 (格式的控制項之 CustomItem 的 ItemSelectionCondition 專案) ExpressionBinding 元素)  (</span><span class="sxs-lookup"><span data-stu-id="f8a8b-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f8a8b-107">語法</span><span class="sxs-lookup"><span data-stu-id="f8a8b-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f8a8b-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f8a8b-108">Attributes and Elements</span></span>

<span data-ttu-id="f8a8b-109">下列各節說明屬性、子專案和元素的父元素 `ItemSelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="f8a8b-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f8a8b-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f8a8b-110">Attributes</span></span>

<span data-ttu-id="f8a8b-111">無。</span><span class="sxs-lookup"><span data-stu-id="f8a8b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f8a8b-112">子元素</span><span class="sxs-lookup"><span data-stu-id="f8a8b-112">Child Elements</span></span>

|<span data-ttu-id="f8a8b-113">元素</span><span class="sxs-lookup"><span data-stu-id="f8a8b-113">Element</span></span>|<span data-ttu-id="f8a8b-114">描述</span><span class="sxs-lookup"><span data-stu-id="f8a8b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f8a8b-115"> (格式之控制項的 ItemSelectionCondition 的 PropertyName 元素) </span><span class="sxs-lookup"><span data-stu-id="f8a8b-115">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f8a8b-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f8a8b-116">Optional element.</span></span><br /><br /> <span data-ttu-id="f8a8b-117">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="f8a8b-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f8a8b-118">設定 (格式之控制項的 ItemSelectionCondition 的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="f8a8b-118">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f8a8b-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f8a8b-119">Optional element.</span></span><br /><br /> <span data-ttu-id="f8a8b-120">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="f8a8b-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f8a8b-121">父項目</span><span class="sxs-lookup"><span data-stu-id="f8a8b-121">Parent Elements</span></span>

|<span data-ttu-id="f8a8b-122">元素</span><span class="sxs-lookup"><span data-stu-id="f8a8b-122">Element</span></span>|<span data-ttu-id="f8a8b-123">描述</span><span class="sxs-lookup"><span data-stu-id="f8a8b-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f8a8b-124">設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="f8a8b-124">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="f8a8b-125">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="f8a8b-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f8a8b-126">備註</span><span class="sxs-lookup"><span data-stu-id="f8a8b-126">Remarks</span></span>

<span data-ttu-id="f8a8b-127">您可以為此條件指定一個屬性名稱或腳本，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="f8a8b-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8a8b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8a8b-128">See Also</span></span>

[<span data-ttu-id="f8a8b-129"> (格式之控制項的 ItemSelectionCondition 的 PropertyName 元素) </span><span class="sxs-lookup"><span data-stu-id="f8a8b-129">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f8a8b-130">設定 (格式之控制項的 ItemSelectionCondition 的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="f8a8b-130">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f8a8b-131">設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="f8a8b-131">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="f8a8b-132">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="f8a8b-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
