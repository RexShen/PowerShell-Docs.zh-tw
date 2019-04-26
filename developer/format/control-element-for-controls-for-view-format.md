---
title: 控制控制項的項目，檢視 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066765"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="11ab4-102">檢視之控制項的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="11ab4-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="11ab4-103">定義可供檢視和名稱，用來參考控制項的控制項。</span><span class="sxs-lookup"><span data-stu-id="11ab4-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="11ab4-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 的檢視 （格式） 控制項的 Controls 項目 （格式） 控制項項目</span><span class="sxs-lookup"><span data-stu-id="11ab4-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="11ab4-105">語法</span><span class="sxs-lookup"><span data-stu-id="11ab4-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="11ab4-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="11ab4-106">Attributes and Elements</span></span>

<span data-ttu-id="11ab4-107">下列各節說明屬性、 子項目和父項目`Control`項目。</span><span class="sxs-lookup"><span data-stu-id="11ab4-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="11ab4-108">屬性</span><span class="sxs-lookup"><span data-stu-id="11ab4-108">Attributes</span></span>

<span data-ttu-id="11ab4-109">無。</span><span class="sxs-lookup"><span data-stu-id="11ab4-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="11ab4-110">子元素</span><span class="sxs-lookup"><span data-stu-id="11ab4-110">Child Elements</span></span>

|<span data-ttu-id="11ab4-111">元素</span><span class="sxs-lookup"><span data-stu-id="11ab4-111">Element</span></span>|<span data-ttu-id="11ab4-112">描述</span><span class="sxs-lookup"><span data-stu-id="11ab4-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11ab4-113">控制項的檢視 （格式） 的 name 元素</span><span class="sxs-lookup"><span data-stu-id="11ab4-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="11ab4-114">必要項目。</span><span class="sxs-lookup"><span data-stu-id="11ab4-114">Required element.</span></span><br /><br /> <span data-ttu-id="11ab4-115">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="11ab4-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="11ab4-116">用於檢視 （格式） 的控制項的控制項 CustomControl 項目</span><span class="sxs-lookup"><span data-stu-id="11ab4-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="11ab4-117">必要項目。</span><span class="sxs-lookup"><span data-stu-id="11ab4-117">Required element.</span></span><br /><br /> <span data-ttu-id="11ab4-118">定義這份檢視所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="11ab4-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="11ab4-119">父項目</span><span class="sxs-lookup"><span data-stu-id="11ab4-119">Parent Elements</span></span>

|<span data-ttu-id="11ab4-120">項目</span><span class="sxs-lookup"><span data-stu-id="11ab4-120">Element</span></span>|<span data-ttu-id="11ab4-121">描述</span><span class="sxs-lookup"><span data-stu-id="11ab4-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11ab4-122">控制項項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="11ab4-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="11ab4-123">定義可供特定檢視的檢視控制項。</span><span class="sxs-lookup"><span data-stu-id="11ab4-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="11ab4-124">備註</span><span class="sxs-lookup"><span data-stu-id="11ab4-124">Remarks</span></span>

<span data-ttu-id="11ab4-125">這個控制項可以指定下列項目：</span><span class="sxs-lookup"><span data-stu-id="11ab4-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="11ab4-126">用於檢視 （格式） 的控制項 ExpressionBinding CustomControlName 項目</span><span class="sxs-lookup"><span data-stu-id="11ab4-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="11ab4-127">CustomControlName CustomControl 檢視 （格式） 的 ExpressionBinding 的項目</span><span class="sxs-lookup"><span data-stu-id="11ab4-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="11ab4-128">CustomControlName ExpressionBinding 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="11ab4-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="11ab4-129">CustomControlName GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="11ab4-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="11ab4-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11ab4-130">See Also</span></span>

[<span data-ttu-id="11ab4-131">用於檢視 （格式） 的控制項的控制項 CustomControl 項目</span><span class="sxs-lookup"><span data-stu-id="11ab4-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="11ab4-132">用於檢視 （格式） 的控制項 ExpressionBinding CustomControlName 項目</span><span class="sxs-lookup"><span data-stu-id="11ab4-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="11ab4-133">CustomControlName CustomControl 檢視 （格式） 的 ExpressionBinding 的項目</span><span class="sxs-lookup"><span data-stu-id="11ab4-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="11ab4-134">CustomControlName ExpressionBinding 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="11ab4-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="11ab4-135">CustomControlName ExpressionBinding 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="11ab4-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="11ab4-136">控制項項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="11ab4-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="11ab4-137">用於檢視 （格式） 的控制項的控制項的 name 元素</span><span class="sxs-lookup"><span data-stu-id="11ab4-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="11ab4-138">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="11ab4-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
