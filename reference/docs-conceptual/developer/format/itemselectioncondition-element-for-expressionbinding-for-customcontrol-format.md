---
title: CustomControl (格式) 的 ExpressionBinding 的 ItemSelectionCondition 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6a5c66a63c02980b16c2d2d9dd689410c8aec51c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781183"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="65b7e-102">CustomControl 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="65b7e-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="65b7e-103">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="65b7e-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="65b7e-104">可以針對控制項專案指定的選取條件數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="65b7e-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="65b7e-105">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="65b7e-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="65b7e-106">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 專案 (格式) CustomControl for view (CustomEntry 元素，CustomEntries for view) format (CustomItem 專案（CustomEntry for view) format (ExpressionBinding 元素）) CustomItem 專案（ (CustomControl 的運算式系結</span><span class="sxs-lookup"><span data-stu-id="65b7e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="65b7e-107">語法</span><span class="sxs-lookup"><span data-stu-id="65b7e-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="65b7e-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="65b7e-108">Attributes and Elements</span></span>

<span data-ttu-id="65b7e-109">下列各節說明屬性、子專案和元素的父元素 `ItemSelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="65b7e-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="65b7e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="65b7e-110">Attributes</span></span>

<span data-ttu-id="65b7e-111">無。</span><span class="sxs-lookup"><span data-stu-id="65b7e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="65b7e-112">子元素</span><span class="sxs-lookup"><span data-stu-id="65b7e-112">Child Elements</span></span>

|<span data-ttu-id="65b7e-113">元素</span><span class="sxs-lookup"><span data-stu-id="65b7e-113">Element</span></span>|<span data-ttu-id="65b7e-114">描述</span><span class="sxs-lookup"><span data-stu-id="65b7e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="65b7e-115">ItemSelectionCondition for CustomControl for View (格式的 PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="65b7e-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="65b7e-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="65b7e-116">Optional element.</span></span><br /><br /> <span data-ttu-id="65b7e-117">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="65b7e-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="65b7e-118">檢視之 CustomControl 的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="65b7e-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="65b7e-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="65b7e-119">Optional element.</span></span><br /><br /> <span data-ttu-id="65b7e-120">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="65b7e-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="65b7e-121">父項目</span><span class="sxs-lookup"><span data-stu-id="65b7e-121">Parent Elements</span></span>

|<span data-ttu-id="65b7e-122">元素</span><span class="sxs-lookup"><span data-stu-id="65b7e-122">Element</span></span>|<span data-ttu-id="65b7e-123">描述</span><span class="sxs-lookup"><span data-stu-id="65b7e-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="65b7e-124">檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="65b7e-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="65b7e-125">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="65b7e-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="65b7e-126">備註</span><span class="sxs-lookup"><span data-stu-id="65b7e-126">Remarks</span></span>

<span data-ttu-id="65b7e-127">您可以為此條件指定一個屬性名稱或腳本，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="65b7e-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="65b7e-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65b7e-128">See Also</span></span>

[<span data-ttu-id="65b7e-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="65b7e-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="65b7e-130">檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="65b7e-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
