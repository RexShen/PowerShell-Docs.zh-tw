---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的控制項元素 (格式)
description: 檢視之控制項的控制項元素 (格式)
ms.openlocfilehash: c48b8b7ecaebfde5e6ed2123b837d92561551766
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668077"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="51887-103">檢視之控制項的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="51887-103">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="51887-104">定義可供視圖使用的控制項，以及用來參考控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="51887-104">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="51887-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) Control 元素 (format) Control 控制項的控制項 (格式) </span><span class="sxs-lookup"><span data-stu-id="51887-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="51887-106">語法</span><span class="sxs-lookup"><span data-stu-id="51887-106">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="51887-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="51887-107">Attributes and Elements</span></span>

<span data-ttu-id="51887-108">下列章節說明屬性、子專案和元素的父元素 `Control` 。</span><span class="sxs-lookup"><span data-stu-id="51887-108">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="51887-109">屬性</span><span class="sxs-lookup"><span data-stu-id="51887-109">Attributes</span></span>

<span data-ttu-id="51887-110">無。</span><span class="sxs-lookup"><span data-stu-id="51887-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="51887-111">子元素</span><span class="sxs-lookup"><span data-stu-id="51887-111">Child Elements</span></span>

|<span data-ttu-id="51887-112">元素</span><span class="sxs-lookup"><span data-stu-id="51887-112">Element</span></span>|<span data-ttu-id="51887-113">描述</span><span class="sxs-lookup"><span data-stu-id="51887-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="51887-114">View (Format 的控制項名稱元素) </span><span class="sxs-lookup"><span data-stu-id="51887-114">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="51887-115">必要元素。</span><span class="sxs-lookup"><span data-stu-id="51887-115">Required element.</span></span><br /><br /> <span data-ttu-id="51887-116">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="51887-116">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="51887-117">檢視之控制項的控制項 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="51887-117">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="51887-118">必要元素。</span><span class="sxs-lookup"><span data-stu-id="51887-118">Required element.</span></span><br /><br /> <span data-ttu-id="51887-119">定義此視圖所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="51887-119">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="51887-120">父項目</span><span class="sxs-lookup"><span data-stu-id="51887-120">Parent Elements</span></span>

|<span data-ttu-id="51887-121">元素</span><span class="sxs-lookup"><span data-stu-id="51887-121">Element</span></span>|<span data-ttu-id="51887-122">描述</span><span class="sxs-lookup"><span data-stu-id="51887-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="51887-123">Controls 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="51887-123">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="51887-124">定義可供特定視圖使用的 view 控制項。</span><span class="sxs-lookup"><span data-stu-id="51887-124">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="51887-125">備註</span><span class="sxs-lookup"><span data-stu-id="51887-125">Remarks</span></span>

<span data-ttu-id="51887-126">此控制項可以由下列元素指定：</span><span class="sxs-lookup"><span data-stu-id="51887-126">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="51887-127">檢視之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="51887-127">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="51887-128">檢視之 CustomControl 的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="51887-128">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="51887-129">GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="51887-129">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="51887-130">GroupBy 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="51887-130">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="51887-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51887-131">See Also</span></span>

[<span data-ttu-id="51887-132">檢視之控制項的控制項 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="51887-132">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="51887-133">檢視之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="51887-133">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="51887-134">檢視之 CustomControl 的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="51887-134">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="51887-135">GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="51887-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="51887-136">GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="51887-136">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="51887-137">Controls 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="51887-137">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="51887-138">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="51887-138">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="51887-139">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="51887-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
