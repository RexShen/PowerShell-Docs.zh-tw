---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)
description: GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)
ms.openlocfilehash: 92120ace5ed316fbfbf1d51422071c27d5a604cf
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651984"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="ade90-103">GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ade90-103">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="ade90-104">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="ade90-104">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="ade90-105">可以針對控制項專案指定的選取條件數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="ade90-105">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="ade90-106">定義如何顯示新的物件群組時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="ade90-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="ade90-107">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 專案的視圖 (格式) CustomEntries 元素用於 GroupBy (格式) 元素用於 CustomEntry 的 groupby (格式) CustomControl 專案用於 CustomItem 的 groupby (格式) CustomEntry 專案的 ExpressionBinding 的 groupby (格式) CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="ade90-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ade90-108">語法</span><span class="sxs-lookup"><span data-stu-id="ade90-108">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ade90-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ade90-109">Attributes and Elements</span></span>

<span data-ttu-id="ade90-110">下列各節說明屬性、子專案和元素的父元素 `ItemSelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="ade90-110">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ade90-111">屬性</span><span class="sxs-lookup"><span data-stu-id="ade90-111">Attributes</span></span>

<span data-ttu-id="ade90-112">無。</span><span class="sxs-lookup"><span data-stu-id="ade90-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ade90-113">子元素</span><span class="sxs-lookup"><span data-stu-id="ade90-113">Child Elements</span></span>

|<span data-ttu-id="ade90-114">元素</span><span class="sxs-lookup"><span data-stu-id="ade90-114">Element</span></span>|<span data-ttu-id="ade90-115">描述</span><span class="sxs-lookup"><span data-stu-id="ade90-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ade90-116">GroupBy 之 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ade90-116">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="ade90-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="ade90-117">Optional element.</span></span><br /><br /> <span data-ttu-id="ade90-118">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="ade90-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="ade90-119">GroupBy 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ade90-119">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="ade90-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="ade90-120">Optional element.</span></span><br /><br /> <span data-ttu-id="ade90-121">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="ade90-121">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ade90-122">父項目</span><span class="sxs-lookup"><span data-stu-id="ade90-122">Parent Elements</span></span>

|<span data-ttu-id="ade90-123">元素</span><span class="sxs-lookup"><span data-stu-id="ade90-123">Element</span></span>|<span data-ttu-id="ade90-124">描述</span><span class="sxs-lookup"><span data-stu-id="ade90-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ade90-125">GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ade90-125">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="ade90-126">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="ade90-126">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ade90-127">備註</span><span class="sxs-lookup"><span data-stu-id="ade90-127">Remarks</span></span>

<span data-ttu-id="ade90-128">您可以為此條件指定一個屬性名稱或腳本，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="ade90-128">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="ade90-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ade90-129">See Also</span></span>

[<span data-ttu-id="ade90-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="ade90-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="ade90-131">GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ade90-131">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
