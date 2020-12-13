---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)
description: 檢視之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)
ms.openlocfilehash: adbe747bdb4f6c1d180e5b630247de0fd3d72b85
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648063"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="db1cc-103">檢視之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="db1cc-103">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="db1cc-104">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="db1cc-104">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="db1cc-105">當定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="db1cc-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="db1cc-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 專案 (格式) 控制項專案 (格式) 控制項專案 () 格式控制項的控制項專案 (格式) CustomEntries 元素用於查看 CustomControl 的視圖 (針對 view (Format 的控制項格式化) CustomEntry 元素) CustomItem 專案 CustomEntry for view 的元素 (格式) ExpressionBinding 專案 CustomItem 的專案 (格式) ItemSelectionCondition 專案的 ExpressionBinding 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="db1cc-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="db1cc-107">語法</span><span class="sxs-lookup"><span data-stu-id="db1cc-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="db1cc-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="db1cc-108">Attributes and Elements</span></span>

<span data-ttu-id="db1cc-109">下列各節說明屬性、子專案和元素的父元素 `ItemSelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="db1cc-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="db1cc-110">屬性</span><span class="sxs-lookup"><span data-stu-id="db1cc-110">Attributes</span></span>

<span data-ttu-id="db1cc-111">無。</span><span class="sxs-lookup"><span data-stu-id="db1cc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="db1cc-112">子元素</span><span class="sxs-lookup"><span data-stu-id="db1cc-112">Child Elements</span></span>

|<span data-ttu-id="db1cc-113">元素</span><span class="sxs-lookup"><span data-stu-id="db1cc-113">Element</span></span>|<span data-ttu-id="db1cc-114">描述</span><span class="sxs-lookup"><span data-stu-id="db1cc-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db1cc-115">檢視之控制項的 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="db1cc-115">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="db1cc-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="db1cc-116">Optional element.</span></span><br /><br /> <span data-ttu-id="db1cc-117">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="db1cc-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="db1cc-118">檢視之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="db1cc-118">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="db1cc-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="db1cc-119">Optional element.</span></span><br /><br /> <span data-ttu-id="db1cc-120">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="db1cc-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="db1cc-121">父項目</span><span class="sxs-lookup"><span data-stu-id="db1cc-121">Parent Elements</span></span>

|<span data-ttu-id="db1cc-122">元素</span><span class="sxs-lookup"><span data-stu-id="db1cc-122">Element</span></span>|<span data-ttu-id="db1cc-123">描述</span><span class="sxs-lookup"><span data-stu-id="db1cc-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db1cc-124">檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="db1cc-124">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="db1cc-125">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="db1cc-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="db1cc-126">備註</span><span class="sxs-lookup"><span data-stu-id="db1cc-126">Remarks</span></span>

<span data-ttu-id="db1cc-127">您可以為此條件指定一個屬性名稱或腳本，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="db1cc-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="db1cc-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db1cc-128">See Also</span></span>

[<span data-ttu-id="db1cc-129">檢視之控制項的 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="db1cc-129">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="db1cc-130">檢視之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="db1cc-130">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="db1cc-131">檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="db1cc-131">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="db1cc-132">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="db1cc-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
