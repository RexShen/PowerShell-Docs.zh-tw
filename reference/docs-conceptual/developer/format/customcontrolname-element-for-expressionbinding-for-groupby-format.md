---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)
description: GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)
ms.openlocfilehash: bb7dbd449137628da1794628c5a7d7e10158dd46
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655435"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="1647a-103">GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1647a-103">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="1647a-104">指定通用控制項或 view 控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="1647a-104">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="1647a-105">定義如何顯示新的物件群組時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="1647a-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="1647a-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 專案的視圖 (格式) CustomEntries 元素用於 GroupBy (格式) 元素用於 CustomEntry 的 groupby (格式) CustomControl 專案用於 CustomItem 的 groupby (格式) CustomEntry 專案的 ExpressionBinding 的 groupby (格式) CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="1647a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1647a-107">語法</span><span class="sxs-lookup"><span data-stu-id="1647a-107">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1647a-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1647a-108">Attributes and Elements</span></span>

<span data-ttu-id="1647a-109">下列各節說明屬性、子專案和元素的父元素 `CustomControlName` 。</span><span class="sxs-lookup"><span data-stu-id="1647a-109">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1647a-110">屬性</span><span class="sxs-lookup"><span data-stu-id="1647a-110">Attributes</span></span>

<span data-ttu-id="1647a-111">無。</span><span class="sxs-lookup"><span data-stu-id="1647a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1647a-112">子元素</span><span class="sxs-lookup"><span data-stu-id="1647a-112">Child Elements</span></span>

<span data-ttu-id="1647a-113">無。</span><span class="sxs-lookup"><span data-stu-id="1647a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1647a-114">父項目</span><span class="sxs-lookup"><span data-stu-id="1647a-114">Parent Elements</span></span>

|<span data-ttu-id="1647a-115">元素</span><span class="sxs-lookup"><span data-stu-id="1647a-115">Element</span></span>|<span data-ttu-id="1647a-116">描述</span><span class="sxs-lookup"><span data-stu-id="1647a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1647a-117">GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1647a-117">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="1647a-118">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="1647a-118">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1647a-119">文字值</span><span class="sxs-lookup"><span data-stu-id="1647a-119">Text Value</span></span>

<span data-ttu-id="1647a-120">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="1647a-120">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="1647a-121">備註</span><span class="sxs-lookup"><span data-stu-id="1647a-121">Remarks</span></span>

<span data-ttu-id="1647a-122">您可以建立可供格式化檔案的所有視圖使用的通用控制項，也可以建立可供特定視圖使用的 view 控制項。</span><span class="sxs-lookup"><span data-stu-id="1647a-122">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="1647a-123">下列元素會指定這些控制項的名稱：</span><span class="sxs-lookup"><span data-stu-id="1647a-123">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="1647a-124">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1647a-124">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="1647a-125">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1647a-125">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="1647a-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1647a-126">See Also</span></span>

[<span data-ttu-id="1647a-127">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1647a-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="1647a-128">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1647a-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="1647a-129">GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1647a-129">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="1647a-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="1647a-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
