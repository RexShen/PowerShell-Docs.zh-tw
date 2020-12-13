---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)
description: 設定之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)
ms.openlocfilehash: 3815956f59f19c0215aaf26b94dede656b9453cb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648319"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="d7281-103">設定之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d7281-103">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="d7281-104">指定通用控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="d7281-104">Specifies the name of a common control.</span></span> <span data-ttu-id="d7281-105">當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="d7281-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="d7281-106">設定元素 (格式) 控制項的設定元素 (格式) 控制項的設定 (格式) CustomControl 元素，用於 CustomControl 的設定 (格式) CustomEntry 元素針對 configuration (格式的控制項的 CustomControl 格式) CustomItem 元素，用於 CustomEntry 的控制項，以設定 (格式的控制項之 CustomItem 的 CustomControlName 專案) ExpressionBinding 元素)  (</span><span class="sxs-lookup"><span data-stu-id="d7281-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d7281-107">語法</span><span class="sxs-lookup"><span data-stu-id="d7281-107">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d7281-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d7281-108">Attributes and Elements</span></span>

<span data-ttu-id="d7281-109">下列各節說明屬性、子專案和元素的父元素 `CustomControlName` 。</span><span class="sxs-lookup"><span data-stu-id="d7281-109">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d7281-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d7281-110">Attributes</span></span>

<span data-ttu-id="d7281-111">無。</span><span class="sxs-lookup"><span data-stu-id="d7281-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d7281-112">子元素</span><span class="sxs-lookup"><span data-stu-id="d7281-112">Child Elements</span></span>

<span data-ttu-id="d7281-113">無。</span><span class="sxs-lookup"><span data-stu-id="d7281-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d7281-114">父項目</span><span class="sxs-lookup"><span data-stu-id="d7281-114">Parent Elements</span></span>

|<span data-ttu-id="d7281-115">元素</span><span class="sxs-lookup"><span data-stu-id="d7281-115">Element</span></span>|<span data-ttu-id="d7281-116">描述</span><span class="sxs-lookup"><span data-stu-id="d7281-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d7281-117">設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d7281-117">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="d7281-118">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="d7281-118">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d7281-119">文字值</span><span class="sxs-lookup"><span data-stu-id="d7281-119">Text Value</span></span>

<span data-ttu-id="d7281-120">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="d7281-120">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7281-121">備註</span><span class="sxs-lookup"><span data-stu-id="d7281-121">Remarks</span></span>

<span data-ttu-id="d7281-122">您可以建立可供格式化檔案的所有視圖使用的通用控制項，也可以建立可供特定視圖使用的 view 控制項。</span><span class="sxs-lookup"><span data-stu-id="d7281-122">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="d7281-123">下列元素會指定這些控制項的名稱：</span><span class="sxs-lookup"><span data-stu-id="d7281-123">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="d7281-124">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d7281-124">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="d7281-125">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d7281-125">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="d7281-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7281-126">See Also</span></span>

[<span data-ttu-id="d7281-127">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d7281-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="d7281-128">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d7281-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="d7281-129">設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d7281-129">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="d7281-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="d7281-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
