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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363467"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="b7678-102">檢視之控制項的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b7678-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="b7678-103">定義可供視圖使用的控制項，以及用來參考控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="b7678-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="b7678-104">設定專案（格式） ViewDefinitions 元素（格式） View 元素（格式）控制項的元素（格式）控制項專案（格式）</span><span class="sxs-lookup"><span data-stu-id="b7678-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b7678-105">語法</span><span class="sxs-lookup"><span data-stu-id="b7678-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b7678-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="b7678-106">Attributes and Elements</span></span>

<span data-ttu-id="b7678-107">下列各節說明屬性、子專案，以及 `Control` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="b7678-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b7678-108">屬性</span><span class="sxs-lookup"><span data-stu-id="b7678-108">Attributes</span></span>

<span data-ttu-id="b7678-109">無。</span><span class="sxs-lookup"><span data-stu-id="b7678-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b7678-110">子元素</span><span class="sxs-lookup"><span data-stu-id="b7678-110">Child Elements</span></span>

|<span data-ttu-id="b7678-111">元素</span><span class="sxs-lookup"><span data-stu-id="b7678-111">Element</span></span>|<span data-ttu-id="b7678-112">描述</span><span class="sxs-lookup"><span data-stu-id="b7678-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7678-113">View 控制項的 Name 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7678-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="b7678-114">必要項目。</span><span class="sxs-lookup"><span data-stu-id="b7678-114">Required element.</span></span><br /><br /> <span data-ttu-id="b7678-115">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="b7678-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="b7678-116">View 控制項的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7678-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="b7678-117">必要項目。</span><span class="sxs-lookup"><span data-stu-id="b7678-117">Required element.</span></span><br /><br /> <span data-ttu-id="b7678-118">定義此視圖所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="b7678-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b7678-119">父元素</span><span class="sxs-lookup"><span data-stu-id="b7678-119">Parent Elements</span></span>

|<span data-ttu-id="b7678-120">元素</span><span class="sxs-lookup"><span data-stu-id="b7678-120">Element</span></span>|<span data-ttu-id="b7678-121">描述</span><span class="sxs-lookup"><span data-stu-id="b7678-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7678-122">Controls 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7678-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="b7678-123">定義可供特定視圖使用的 view 控制項。</span><span class="sxs-lookup"><span data-stu-id="b7678-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b7678-124">備註</span><span class="sxs-lookup"><span data-stu-id="b7678-124">Remarks</span></span>

<span data-ttu-id="b7678-125">這個控制項可以由下列元素指定：</span><span class="sxs-lookup"><span data-stu-id="b7678-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="b7678-126">View 之控制項的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7678-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="b7678-127">CustomControl for View 的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7678-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="b7678-128">GroupBy 之 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7678-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="b7678-129">GroupBy 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7678-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="b7678-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7678-130">See Also</span></span>

[<span data-ttu-id="b7678-131">View 控制項的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7678-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="b7678-132">View 之控制項的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7678-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="b7678-133">CustomControl for View 的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7678-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b7678-134">GroupBy 之 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7678-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b7678-135">GroupBy 之 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7678-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b7678-136">Controls 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7678-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="b7678-137">View 控制項控制項的 Name 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7678-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="b7678-138">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="b7678-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
