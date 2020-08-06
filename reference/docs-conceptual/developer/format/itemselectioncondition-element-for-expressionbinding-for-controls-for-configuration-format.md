---
title: ExpressionBinding 之控制項的 ItemSelectionCondition 元素，用於設定 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3bfd3efe916b4d88c024de8f959482cab515f777
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781217"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="835f8-102">設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="835f8-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="835f8-103">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="835f8-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="835f8-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="835f8-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="835f8-105">Configuration 元素 (格式) Controls 設定的控制項元素 (格式設定的控制項) 控制項專案 (格式) 設定 (格式的 CustomControl 的 CustomEntries 元素) CustomEntry 元素如需設定 (格式的控制項的 CustomControl) CustomItem 元素用於 CustomEntry 的 configuration ExpressionBinding 元素) CustomItem 的 ItemSelectionCondition 元素設定 (格式的控制項)  (</span><span class="sxs-lookup"><span data-stu-id="835f8-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="835f8-106">語法</span><span class="sxs-lookup"><span data-stu-id="835f8-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="835f8-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="835f8-107">Attributes and Elements</span></span>

<span data-ttu-id="835f8-108">下列各節說明屬性、子專案和元素的父元素 `ItemSelectionCondition` 。</span><span class="sxs-lookup"><span data-stu-id="835f8-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="835f8-109">屬性</span><span class="sxs-lookup"><span data-stu-id="835f8-109">Attributes</span></span>

<span data-ttu-id="835f8-110">無。</span><span class="sxs-lookup"><span data-stu-id="835f8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="835f8-111">子元素</span><span class="sxs-lookup"><span data-stu-id="835f8-111">Child Elements</span></span>

|<span data-ttu-id="835f8-112">元素</span><span class="sxs-lookup"><span data-stu-id="835f8-112">Element</span></span>|<span data-ttu-id="835f8-113">描述</span><span class="sxs-lookup"><span data-stu-id="835f8-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="835f8-114">設定 (格式之控制項的 ItemSelectionCondition 的 PropertyName 元素) </span><span class="sxs-lookup"><span data-stu-id="835f8-114">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="835f8-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="835f8-115">Optional element.</span></span><br /><br /> <span data-ttu-id="835f8-116">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="835f8-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="835f8-117">設定 (格式之控制項的 ItemSelectionCondition 的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="835f8-117">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="835f8-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="835f8-118">Optional element.</span></span><br /><br /> <span data-ttu-id="835f8-119">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="835f8-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="835f8-120">父項目</span><span class="sxs-lookup"><span data-stu-id="835f8-120">Parent Elements</span></span>

|<span data-ttu-id="835f8-121">元素</span><span class="sxs-lookup"><span data-stu-id="835f8-121">Element</span></span>|<span data-ttu-id="835f8-122">描述</span><span class="sxs-lookup"><span data-stu-id="835f8-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="835f8-123">設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="835f8-123">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="835f8-124">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="835f8-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="835f8-125">備註</span><span class="sxs-lookup"><span data-stu-id="835f8-125">Remarks</span></span>

<span data-ttu-id="835f8-126">您可以為此條件指定一個屬性名稱或腳本，但不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="835f8-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="835f8-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="835f8-127">See Also</span></span>

[<span data-ttu-id="835f8-128">設定 (格式之控制項的 ItemSelectionCondition 的 PropertyName 元素) </span><span class="sxs-lookup"><span data-stu-id="835f8-128">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="835f8-129">設定 (格式之控制項的 ItemSelectionCondition 的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="835f8-129">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="835f8-130">設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="835f8-130">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="835f8-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="835f8-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
