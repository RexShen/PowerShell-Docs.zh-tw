---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之 CustomControl 的 ExpressionBinding 的 CustomControlName 元素 (格式)
description: 檢視之 CustomControl 的 ExpressionBinding 的 CustomControlName 元素 (格式)
ms.openlocfilehash: 24b27428c07d7178f0069f6d0e5b7ffc555efe34
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666802"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="498ef-103">檢視之 CustomControl 的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="498ef-103">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="498ef-104">指定通用控制項或 view 控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="498ef-104">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="498ef-105">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="498ef-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="498ef-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) CustomControl 元素 for View (format) CustomEntries 元素 for view (format) 元素 for CustomEntry for view (format) CustomEntries 專案 for CustomItem (format) CustomEntry 元素 for ExpressionBinding (format 的運算式系結) CustomItem 專案 (</span><span class="sxs-lookup"><span data-stu-id="498ef-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="498ef-107">語法</span><span class="sxs-lookup"><span data-stu-id="498ef-107">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="498ef-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="498ef-108">Attributes and Elements</span></span>

<span data-ttu-id="498ef-109">下列各節說明屬性、子專案和元素的父元素 `CustomControlName` 。</span><span class="sxs-lookup"><span data-stu-id="498ef-109">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="498ef-110">屬性</span><span class="sxs-lookup"><span data-stu-id="498ef-110">Attributes</span></span>

<span data-ttu-id="498ef-111">無。</span><span class="sxs-lookup"><span data-stu-id="498ef-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="498ef-112">子元素</span><span class="sxs-lookup"><span data-stu-id="498ef-112">Child Elements</span></span>

<span data-ttu-id="498ef-113">無。</span><span class="sxs-lookup"><span data-stu-id="498ef-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="498ef-114">父項目</span><span class="sxs-lookup"><span data-stu-id="498ef-114">Parent Elements</span></span>

|<span data-ttu-id="498ef-115">元素</span><span class="sxs-lookup"><span data-stu-id="498ef-115">Element</span></span>|<span data-ttu-id="498ef-116">描述</span><span class="sxs-lookup"><span data-stu-id="498ef-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="498ef-117">CustomItem (格式的 ExpressionBinding 元素) </span><span class="sxs-lookup"><span data-stu-id="498ef-117">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="498ef-118">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="498ef-118">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="498ef-119">文字值</span><span class="sxs-lookup"><span data-stu-id="498ef-119">Text Value</span></span>

<span data-ttu-id="498ef-120">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="498ef-120">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="498ef-121">備註</span><span class="sxs-lookup"><span data-stu-id="498ef-121">Remarks</span></span>

<span data-ttu-id="498ef-122">您可以建立可供格式化檔案的所有視圖使用的通用控制項，也可以建立可供特定視圖使用的 view 控制項。</span><span class="sxs-lookup"><span data-stu-id="498ef-122">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="498ef-123">這些控制項的名稱是由下列元素所指定。</span><span class="sxs-lookup"><span data-stu-id="498ef-123">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="498ef-124">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="498ef-124">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="498ef-125">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="498ef-125">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="498ef-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="498ef-126">See Also</span></span>

[<span data-ttu-id="498ef-127">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="498ef-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="498ef-128">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="498ef-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="498ef-129">CustomItem (格式的 ExpressionBinding 元素) </span><span class="sxs-lookup"><span data-stu-id="498ef-129">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="498ef-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="498ef-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
