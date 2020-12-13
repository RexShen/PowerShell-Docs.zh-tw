---
ms.date: 09/13/2016
ms.topic: reference
title: CustomControl 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)
description: CustomControl 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)
ms.openlocfilehash: 38c88ad47e57cd20902c6b8aabdb0b8e8b682ba4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648032"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="7ae73-103">CustomControl 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7ae73-103">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="7ae73-104">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="7ae73-104">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="7ae73-105">可以針對控制項專案指定的選取條件數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="7ae73-105">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="7ae73-106">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="7ae73-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="7ae73-107">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) CustomControl 專案 (格式) CustomEntries 專案 (格式) 元素 (格式) 專案 (格式) CustomEntry 專案 for CustomEntries for view (format) CustomItem 專案 for CustomEntry for view (格式) ExpressionBinding 專案 CustomItem 的運算式系結 CustomControl 元素</span><span class="sxs-lookup"><span data-stu-id="7ae73-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7ae73-108">語法</span><span class="sxs-lookup"><span data-stu-id="7ae73-108">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7ae73-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7ae73-109">Attributes and Elements</span></span>

<span data-ttu-id="7ae73-110">下列各節說明屬性、子專案和元素的父元素 `ItemSelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="7ae73-110">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7ae73-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7ae73-111">Attributes</span></span>

<span data-ttu-id="7ae73-112">無。</span><span class="sxs-lookup"><span data-stu-id="7ae73-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7ae73-113">子元素</span><span class="sxs-lookup"><span data-stu-id="7ae73-113">Child Elements</span></span>

|<span data-ttu-id="7ae73-114">元素</span><span class="sxs-lookup"><span data-stu-id="7ae73-114">Element</span></span>|<span data-ttu-id="7ae73-115">描述</span><span class="sxs-lookup"><span data-stu-id="7ae73-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7ae73-116">View (格式之 CustomControl 的 ItemSelectionCondition 的 PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="7ae73-116">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="7ae73-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="7ae73-117">Optional element.</span></span><br /><br /> <span data-ttu-id="7ae73-118">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="7ae73-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="7ae73-119">檢視之 CustomControl 的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7ae73-119">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="7ae73-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="7ae73-120">Optional element.</span></span><br /><br /> <span data-ttu-id="7ae73-121">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="7ae73-121">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7ae73-122">父項目</span><span class="sxs-lookup"><span data-stu-id="7ae73-122">Parent Elements</span></span>

|<span data-ttu-id="7ae73-123">元素</span><span class="sxs-lookup"><span data-stu-id="7ae73-123">Element</span></span>|<span data-ttu-id="7ae73-124">描述</span><span class="sxs-lookup"><span data-stu-id="7ae73-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7ae73-125">檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7ae73-125">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="7ae73-126">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="7ae73-126">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7ae73-127">備註</span><span class="sxs-lookup"><span data-stu-id="7ae73-127">Remarks</span></span>

<span data-ttu-id="7ae73-128">您可以為此條件指定一個屬性名稱或腳本，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="7ae73-128">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ae73-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ae73-129">See Also</span></span>

[<span data-ttu-id="7ae73-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="7ae73-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="7ae73-131">檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7ae73-131">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
