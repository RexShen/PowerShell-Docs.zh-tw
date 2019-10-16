---
title: View 控制項的控制項元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363467"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="e233c-102">檢視之控制項的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e233c-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="e233c-103">定義可供視圖使用的控制項，以及用來參考控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="e233c-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="e233c-104">設定專案（格式） ViewDefinitions 元素（格式） View 元素（格式）控制項的元素（格式）控制項專案（格式）</span><span class="sxs-lookup"><span data-stu-id="e233c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e233c-105">語法</span><span class="sxs-lookup"><span data-stu-id="e233c-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e233c-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="e233c-106">Attributes and Elements</span></span>

<span data-ttu-id="e233c-107">下列各節說明屬性、子專案，以及 `Control` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="e233c-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e233c-108">屬性</span><span class="sxs-lookup"><span data-stu-id="e233c-108">Attributes</span></span>

<span data-ttu-id="e233c-109">無。</span><span class="sxs-lookup"><span data-stu-id="e233c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e233c-110">子元素</span><span class="sxs-lookup"><span data-stu-id="e233c-110">Child Elements</span></span>

|<span data-ttu-id="e233c-111">元素</span><span class="sxs-lookup"><span data-stu-id="e233c-111">Element</span></span>|<span data-ttu-id="e233c-112">描述</span><span class="sxs-lookup"><span data-stu-id="e233c-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e233c-113">View 控制項的 Name 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e233c-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="e233c-114">必要元素。</span><span class="sxs-lookup"><span data-stu-id="e233c-114">Required element.</span></span><br /><br /> <span data-ttu-id="e233c-115">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="e233c-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="e233c-116">View 控制項的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e233c-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="e233c-117">必要元素。</span><span class="sxs-lookup"><span data-stu-id="e233c-117">Required element.</span></span><br /><br /> <span data-ttu-id="e233c-118">定義此視圖所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="e233c-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e233c-119">父元素</span><span class="sxs-lookup"><span data-stu-id="e233c-119">Parent Elements</span></span>

|<span data-ttu-id="e233c-120">元素</span><span class="sxs-lookup"><span data-stu-id="e233c-120">Element</span></span>|<span data-ttu-id="e233c-121">描述</span><span class="sxs-lookup"><span data-stu-id="e233c-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e233c-122">Controls 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e233c-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="e233c-123">定義可供特定視圖使用的 view 控制項。</span><span class="sxs-lookup"><span data-stu-id="e233c-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e233c-124">備註</span><span class="sxs-lookup"><span data-stu-id="e233c-124">Remarks</span></span>

<span data-ttu-id="e233c-125">這個控制項可以由下列元素指定：</span><span class="sxs-lookup"><span data-stu-id="e233c-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="e233c-126">View 之控制項的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e233c-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="e233c-127">CustomControl for View 的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e233c-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="e233c-128">GroupBy 之 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e233c-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="e233c-129">GroupBy 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e233c-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="e233c-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e233c-130">See Also</span></span>

[<span data-ttu-id="e233c-131">View 控制項的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e233c-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="e233c-132">View 之控制項的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e233c-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="e233c-133">CustomControl for View 的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e233c-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e233c-134">GroupBy 之 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e233c-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="e233c-135">GroupBy 之 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e233c-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="e233c-136">Controls 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e233c-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="e233c-137">View 控制項控制項的 Name 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e233c-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="e233c-138">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="e233c-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
