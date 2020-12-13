---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的控制項的名稱元素 (格式)
description: 設定之控制項的控制項的名稱元素 (格式)
ms.openlocfilehash: 0c1c83f827482886ca742f2c0174e8383f87fb52
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666496"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="a99de-103">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a99de-103">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="a99de-104">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="a99de-104">Specifies the name of the control.</span></span> <span data-ttu-id="a99de-105">當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="a99de-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="a99de-106">Configuration 專案 (格式) 控制項的設定 (格式設定 (格式的控制項元素) 控制項，以控制) 格式的控制項 (</span><span class="sxs-lookup"><span data-stu-id="a99de-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a99de-107">語法</span><span class="sxs-lookup"><span data-stu-id="a99de-107">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="a99de-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a99de-108">Attributes and Elements</span></span>

<span data-ttu-id="a99de-109">下列各節說明屬性、子專案和元素的父元素 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="a99de-109">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a99de-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a99de-110">Attributes</span></span>

<span data-ttu-id="a99de-111">無。</span><span class="sxs-lookup"><span data-stu-id="a99de-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a99de-112">子元素</span><span class="sxs-lookup"><span data-stu-id="a99de-112">Child Elements</span></span>

<span data-ttu-id="a99de-113">無。</span><span class="sxs-lookup"><span data-stu-id="a99de-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a99de-114">父項目</span><span class="sxs-lookup"><span data-stu-id="a99de-114">Parent Elements</span></span>

|<span data-ttu-id="a99de-115">元素</span><span class="sxs-lookup"><span data-stu-id="a99de-115">Element</span></span>|<span data-ttu-id="a99de-116">描述</span><span class="sxs-lookup"><span data-stu-id="a99de-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a99de-117">設定之控制項的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a99de-117">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="a99de-118">定義通用控制項，可供格式化檔案的所有視圖和用來參考控制項的名稱使用。</span><span class="sxs-lookup"><span data-stu-id="a99de-118">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a99de-119">文字值</span><span class="sxs-lookup"><span data-stu-id="a99de-119">Text Value</span></span>

<span data-ttu-id="a99de-120">指定用來參考此控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="a99de-120">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="a99de-121">備註</span><span class="sxs-lookup"><span data-stu-id="a99de-121">Remarks</span></span>

<span data-ttu-id="a99de-122">此處指定的名稱可用於下列元素，以參考此控制項。</span><span class="sxs-lookup"><span data-stu-id="a99de-122">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="a99de-123">當您建立資料表、清單、寬或自訂控制項時，您可以透過下列元素指定控制項： [view (格式的 GroupBy 元素) ](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="a99de-123">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="a99de-124">建立另一個通用控制項時，此控制項可以由下列元素指定：適用于 [CustomItem 的 ExpressionBinding 元素，用於設定 (格式的控制項) ](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="a99de-124">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="a99de-125">建立可供視圖使用的控制項時，此控制項可以由下列元素指定： [view (格式之控制項的 CustomItem 的 ExpressionBinding 元素) ](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="a99de-125">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="a99de-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a99de-126">See Also</span></span>

[<span data-ttu-id="a99de-127">設定之控制項的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a99de-127">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="a99de-128">設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a99de-128">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="a99de-129">檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a99de-129">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="a99de-130">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a99de-130">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="a99de-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="a99de-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
