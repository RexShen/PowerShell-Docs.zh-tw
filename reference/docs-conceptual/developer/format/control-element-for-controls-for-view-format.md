---
title: View (格式) 控制項的控制項元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 13ea2f09aec7fea8e5460197f133b5f5219cd369
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783801"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="ffe8d-102">檢視之控制項的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ffe8d-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="ffe8d-103">定義可供視圖使用的控制項，以及用來參考控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="ffe8d-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="ffe8d-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) Controls 元素 (格式控制項的) 控制項專案 (格式) </span><span class="sxs-lookup"><span data-stu-id="ffe8d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ffe8d-105">語法</span><span class="sxs-lookup"><span data-stu-id="ffe8d-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ffe8d-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ffe8d-106">Attributes and Elements</span></span>

<span data-ttu-id="ffe8d-107">下列各節說明屬性、子專案和元素的父元素 `Control` 。</span><span class="sxs-lookup"><span data-stu-id="ffe8d-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ffe8d-108">屬性</span><span class="sxs-lookup"><span data-stu-id="ffe8d-108">Attributes</span></span>

<span data-ttu-id="ffe8d-109">無。</span><span class="sxs-lookup"><span data-stu-id="ffe8d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ffe8d-110">子元素</span><span class="sxs-lookup"><span data-stu-id="ffe8d-110">Child Elements</span></span>

|<span data-ttu-id="ffe8d-111">元素</span><span class="sxs-lookup"><span data-stu-id="ffe8d-111">Element</span></span>|<span data-ttu-id="ffe8d-112">描述</span><span class="sxs-lookup"><span data-stu-id="ffe8d-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ffe8d-113">View (格式之控制項的 Name 元素) </span><span class="sxs-lookup"><span data-stu-id="ffe8d-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="ffe8d-114">必要元素。</span><span class="sxs-lookup"><span data-stu-id="ffe8d-114">Required element.</span></span><br /><br /> <span data-ttu-id="ffe8d-115">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="ffe8d-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="ffe8d-116">檢視之控制項的控制項 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ffe8d-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="ffe8d-117">必要元素。</span><span class="sxs-lookup"><span data-stu-id="ffe8d-117">Required element.</span></span><br /><br /> <span data-ttu-id="ffe8d-118">定義此視圖所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="ffe8d-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ffe8d-119">父項目</span><span class="sxs-lookup"><span data-stu-id="ffe8d-119">Parent Elements</span></span>

|<span data-ttu-id="ffe8d-120">元素</span><span class="sxs-lookup"><span data-stu-id="ffe8d-120">Element</span></span>|<span data-ttu-id="ffe8d-121">描述</span><span class="sxs-lookup"><span data-stu-id="ffe8d-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ffe8d-122">Controls 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="ffe8d-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="ffe8d-123">定義可供特定視圖使用的 view 控制項。</span><span class="sxs-lookup"><span data-stu-id="ffe8d-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ffe8d-124">備註</span><span class="sxs-lookup"><span data-stu-id="ffe8d-124">Remarks</span></span>

<span data-ttu-id="ffe8d-125">這個控制項可以由下列元素指定：</span><span class="sxs-lookup"><span data-stu-id="ffe8d-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="ffe8d-126">檢視之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ffe8d-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="ffe8d-127">檢視之 CustomControl 的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ffe8d-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="ffe8d-128">GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ffe8d-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="ffe8d-129">GroupBy 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ffe8d-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="ffe8d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffe8d-130">See Also</span></span>

[<span data-ttu-id="ffe8d-131">檢視之控制項的控制項 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ffe8d-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="ffe8d-132">檢視之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ffe8d-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="ffe8d-133">檢視之 CustomControl 的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ffe8d-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ffe8d-134">GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ffe8d-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="ffe8d-135">GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ffe8d-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="ffe8d-136">Controls 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="ffe8d-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="ffe8d-137">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ffe8d-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="ffe8d-138">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="ffe8d-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
