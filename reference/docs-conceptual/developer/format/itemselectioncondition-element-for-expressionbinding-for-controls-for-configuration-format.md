---
title: 設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362917"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="c17d4-102">設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c17d4-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="c17d4-103">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="c17d4-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="c17d4-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="c17d4-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="c17d4-105">Configuration 元素（格式）控制設定（format） CustomControl 元素的設定（格式）控制項專案的設定專案（格式） CustomControl 設定的 CustomEntries 元素（格式）Format） CustomEntry 元素，用於 CustomControl 控制項的 CustomItem 元素，用於 CustomEntry 的 configuration ExpressionBinding 元素設定的 CustomItem 專案的控制項（格式）設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c17d4-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c17d4-106">語法</span><span class="sxs-lookup"><span data-stu-id="c17d4-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c17d4-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="c17d4-107">Attributes and Elements</span></span>

<span data-ttu-id="c17d4-108">下列各節說明屬性、子專案，以及 `ItemSelectionCondition` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="c17d4-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c17d4-109">屬性</span><span class="sxs-lookup"><span data-stu-id="c17d4-109">Attributes</span></span>

<span data-ttu-id="c17d4-110">無。</span><span class="sxs-lookup"><span data-stu-id="c17d4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c17d4-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c17d4-111">Child Elements</span></span>

|<span data-ttu-id="c17d4-112">元素</span><span class="sxs-lookup"><span data-stu-id="c17d4-112">Element</span></span>|<span data-ttu-id="c17d4-113">描述</span><span class="sxs-lookup"><span data-stu-id="c17d4-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c17d4-114">設定之控制項的 ItemSelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c17d4-114">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="c17d4-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="c17d4-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c17d4-116">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="c17d4-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="c17d4-117">設定之控制項的 ItemSelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c17d4-117">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="c17d4-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="c17d4-118">Optional element.</span></span><br /><br /> <span data-ttu-id="c17d4-119">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="c17d4-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c17d4-120">父元素</span><span class="sxs-lookup"><span data-stu-id="c17d4-120">Parent Elements</span></span>

|<span data-ttu-id="c17d4-121">元素</span><span class="sxs-lookup"><span data-stu-id="c17d4-121">Element</span></span>|<span data-ttu-id="c17d4-122">描述</span><span class="sxs-lookup"><span data-stu-id="c17d4-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c17d4-123">設定之控制項的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c17d4-123">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="c17d4-124">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="c17d4-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c17d4-125">備註</span><span class="sxs-lookup"><span data-stu-id="c17d4-125">Remarks</span></span>

<span data-ttu-id="c17d4-126">您可以為此條件指定一個屬性名稱或腳本，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="c17d4-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="c17d4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c17d4-127">See Also</span></span>

[<span data-ttu-id="c17d4-128">設定之控制項的 ItemSelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c17d4-128">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="c17d4-129">設定之控制項的 ItemSelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c17d4-129">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="c17d4-130">設定之控制項的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c17d4-130">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="c17d4-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="c17d4-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
