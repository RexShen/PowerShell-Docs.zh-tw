---
title: CustomControl for View (格式) 的 CustomItem 的 ExpressionBinding 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1885a2820c0cb250aa6fda80544f58d06136cfeb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773788"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="32389-102">檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="32389-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="32389-103">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="32389-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="32389-104">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="32389-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="32389-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) CustomControl 元素 for view (format) CustomEntries 專案 for view (格式) CustomEntry 元素 for CustomEntries for CustomControl for view (format) CustomItem 元素，CustomEntry for CustomControl for view (格式) </span><span class="sxs-lookup"><span data-stu-id="32389-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="32389-106">語法</span><span class="sxs-lookup"><span data-stu-id="32389-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="32389-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="32389-107">Attributes and Elements</span></span>

<span data-ttu-id="32389-108">下列各節說明屬性、子專案和元素的父元素 `ExpressionBinding` 。</span><span class="sxs-lookup"><span data-stu-id="32389-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="32389-109">屬性</span><span class="sxs-lookup"><span data-stu-id="32389-109">Attributes</span></span>

<span data-ttu-id="32389-110">無。</span><span class="sxs-lookup"><span data-stu-id="32389-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="32389-111">子元素</span><span class="sxs-lookup"><span data-stu-id="32389-111">Child Elements</span></span>

|<span data-ttu-id="32389-112">元素</span><span class="sxs-lookup"><span data-stu-id="32389-112">Element</span></span>|<span data-ttu-id="32389-113">描述</span><span class="sxs-lookup"><span data-stu-id="32389-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="32389-114">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="32389-114">Optional element.</span></span><br /><br /> <span data-ttu-id="32389-115">定義此控制項所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="32389-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="32389-116">檢視之 CustomControl 的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="32389-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="32389-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="32389-117">Optional element.</span></span><br /><br /> <span data-ttu-id="32389-118">指定通用控制項或 view 控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="32389-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="32389-119">檢視之 CustomControl 的 ExpressionBinding 的 EnumerateCollection 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="32389-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="32389-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="32389-120">Optional element.</span></span><br /><br /> <span data-ttu-id="32389-121">指定會顯示集合的元素。</span><span class="sxs-lookup"><span data-stu-id="32389-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="32389-122">CustomControl for View (格式) 的 ExpressionBinding 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="32389-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="32389-123">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="32389-123">Optional element.</span></span><br /><br /> <span data-ttu-id="32389-124">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="32389-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="32389-125">檢視之 CustomControl 的 ExpressionBinding 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="32389-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="32389-126">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="32389-126">Optional element.</span></span><br /><br /> <span data-ttu-id="32389-127">指定控制項顯示其值的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="32389-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="32389-128">ExpressionBinding for CustomCustomControl for View (Format 的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="32389-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="32389-129">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="32389-129">Optional element.</span></span><br /><br /> <span data-ttu-id="32389-130">指定控制項顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="32389-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="32389-131">父項目</span><span class="sxs-lookup"><span data-stu-id="32389-131">Parent Elements</span></span>

|<span data-ttu-id="32389-132">元素</span><span class="sxs-lookup"><span data-stu-id="32389-132">Element</span></span>|<span data-ttu-id="32389-133">描述</span><span class="sxs-lookup"><span data-stu-id="32389-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="32389-134">檢視之 CustomControl 的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="32389-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="32389-135">定義自訂控制項視圖顯示的資料，以及顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="32389-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="32389-136">備註</span><span class="sxs-lookup"><span data-stu-id="32389-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="32389-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32389-137">See Also</span></span>

[<span data-ttu-id="32389-138">檢視之 CustomControl 的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="32389-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="32389-139">檢視之 CustomControl 的 ExpressionBinding 的 EnumerateCollection 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="32389-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="32389-140">CustomControl for View (格式) 的 ExpressionBinding 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="32389-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="32389-141">檢視之 CustomControl 的 ExpressionBinding 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="32389-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="32389-142">檢視之 CustomControl 的 ExpressionBinding 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="32389-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="32389-143">檢視之 CustomControl 的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="32389-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="32389-144">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="32389-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
