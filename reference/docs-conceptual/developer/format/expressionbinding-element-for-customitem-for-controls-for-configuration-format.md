---
title: CustomItem 之控制項的 ExpressionBinding 元素，用於設定 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1ad83fa9d915822eaefb490658f8a219defdddf2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773907"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="8785d-102">設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8785d-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="8785d-103">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="8785d-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="8785d-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="8785d-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="8785d-105">Configuration 專案 (格式) 控制設定的控制項元素 (格式設定 (格式的控制項) 控制元素) 設定 (格式的 CustomControl 的 CustomEntries 元素) 設定 (格式) CustomControl 元素適用于設定 (格式的控制項 CustomItem 的 Configuration CustomEntry 元素的 ExpressionBinding 專案) 的控制</span><span class="sxs-lookup"><span data-stu-id="8785d-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8785d-106">語法</span><span class="sxs-lookup"><span data-stu-id="8785d-106">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8785d-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8785d-107">Attributes and Elements</span></span>

<span data-ttu-id="8785d-108">下列各節說明屬性、子專案和元素的父元素 `ExpressionBinding` 。</span><span class="sxs-lookup"><span data-stu-id="8785d-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8785d-109">屬性</span><span class="sxs-lookup"><span data-stu-id="8785d-109">Attributes</span></span>

<span data-ttu-id="8785d-110">無。</span><span class="sxs-lookup"><span data-stu-id="8785d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8785d-111">子元素</span><span class="sxs-lookup"><span data-stu-id="8785d-111">Child Elements</span></span>

|<span data-ttu-id="8785d-112">元素</span><span class="sxs-lookup"><span data-stu-id="8785d-112">Element</span></span>|<span data-ttu-id="8785d-113">描述</span><span class="sxs-lookup"><span data-stu-id="8785d-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="8785d-114">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="8785d-114">Optional element.</span></span><br /><br /> <span data-ttu-id="8785d-115">定義此控制項所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="8785d-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="8785d-116">設定之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8785d-116">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="8785d-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="8785d-117">Optional element.</span></span><br /><br /> <span data-ttu-id="8785d-118">指定通用控制項或 view 控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="8785d-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="8785d-119">設定之控制項的 ExpressionBinding 的 EnumerateCollection 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8785d-119">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="8785d-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="8785d-120">Optional element.</span></span><br /><br /> <span data-ttu-id="8785d-121">指定控制項會顯示集合的元素。</span><span class="sxs-lookup"><span data-stu-id="8785d-121">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="8785d-122">設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8785d-122">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="8785d-123">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="8785d-123">Optional element.</span></span><br /><br /> <span data-ttu-id="8785d-124">定義必須存在的條件，才能使用此通用控制項。</span><span class="sxs-lookup"><span data-stu-id="8785d-124">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="8785d-125">設定之控制項的 ExpressionBinding 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8785d-125">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="8785d-126">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="8785d-126">Optional element.</span></span><br /><br /> <span data-ttu-id="8785d-127">指定由通用控制項顯示其值的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="8785d-127">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="8785d-128">設定之控制項的 ExpressionBinding 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8785d-128">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="8785d-129">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="8785d-129">Optional element.</span></span><br /><br /> <span data-ttu-id="8785d-130">指定由通用控制項顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="8785d-130">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8785d-131">父項目</span><span class="sxs-lookup"><span data-stu-id="8785d-131">Parent Elements</span></span>

|<span data-ttu-id="8785d-132">元素</span><span class="sxs-lookup"><span data-stu-id="8785d-132">Element</span></span>|<span data-ttu-id="8785d-133">描述</span><span class="sxs-lookup"><span data-stu-id="8785d-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8785d-134">設定之控制項的 CustomEntry 的 CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="8785d-134">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="8785d-135">定義自訂控制項視圖顯示的資料，以及顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="8785d-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8785d-136">備註</span><span class="sxs-lookup"><span data-stu-id="8785d-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="8785d-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8785d-137">See Also</span></span>

[<span data-ttu-id="8785d-138">設定之控制項的 CustomEntry 的 CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="8785d-138">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="8785d-139">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="8785d-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
