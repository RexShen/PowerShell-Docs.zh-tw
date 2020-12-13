---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)
description: 檢視之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)
ms.openlocfilehash: 35e1554a9eed491f37499a7455e9c5cae3cd9e1e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655459"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="3cdb2-103">檢視之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3cdb2-103">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="3cdb2-104">指定通用控制項或 view 控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="3cdb2-104">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="3cdb2-105">當定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="3cdb2-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="3cdb2-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 專案 (格式) 控制項專案 (格式) 控制項專案 () 格式控制項的控制項專案 (格式) CustomEntries 元素用於查看 CustomControl 的視圖 (針對 view (Format) CustomEntry 元素格式化格式) CustomItem 專案 CustomEntry for view 的控制項 (格式) ExpressionBinding 專案 CustomItem for view 的控制項 (格式) CustomControlName 專案的 ExpressionBindine 元素 (格式的控制項) </span><span class="sxs-lookup"><span data-stu-id="3cdb2-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3cdb2-107">語法</span><span class="sxs-lookup"><span data-stu-id="3cdb2-107">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3cdb2-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3cdb2-108">Attributes and Elements</span></span>

<span data-ttu-id="3cdb2-109">下列各節說明屬性、子專案和元素的父元素 `CustomControlName` 。</span><span class="sxs-lookup"><span data-stu-id="3cdb2-109">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3cdb2-110">屬性</span><span class="sxs-lookup"><span data-stu-id="3cdb2-110">Attributes</span></span>

<span data-ttu-id="3cdb2-111">無。</span><span class="sxs-lookup"><span data-stu-id="3cdb2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3cdb2-112">子元素</span><span class="sxs-lookup"><span data-stu-id="3cdb2-112">Child Elements</span></span>

<span data-ttu-id="3cdb2-113">無。</span><span class="sxs-lookup"><span data-stu-id="3cdb2-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3cdb2-114">父項目</span><span class="sxs-lookup"><span data-stu-id="3cdb2-114">Parent Elements</span></span>

|<span data-ttu-id="3cdb2-115">元素</span><span class="sxs-lookup"><span data-stu-id="3cdb2-115">Element</span></span>|<span data-ttu-id="3cdb2-116">描述</span><span class="sxs-lookup"><span data-stu-id="3cdb2-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3cdb2-117">檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3cdb2-117">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="3cdb2-118">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="3cdb2-118">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3cdb2-119">文字值</span><span class="sxs-lookup"><span data-stu-id="3cdb2-119">Text Value</span></span>

<span data-ttu-id="3cdb2-120">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="3cdb2-120">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="3cdb2-121">備註</span><span class="sxs-lookup"><span data-stu-id="3cdb2-121">Remarks</span></span>

<span data-ttu-id="3cdb2-122">您可以建立可供格式化檔案的所有視圖使用的通用控制項，也可以建立可供特定視圖使用的 view 控制項。</span><span class="sxs-lookup"><span data-stu-id="3cdb2-122">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="3cdb2-123">下列元素會指定這些控制項的名稱：</span><span class="sxs-lookup"><span data-stu-id="3cdb2-123">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="3cdb2-124">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3cdb2-124">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="3cdb2-125">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3cdb2-125">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="3cdb2-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cdb2-126">See Also</span></span>

[<span data-ttu-id="3cdb2-127">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3cdb2-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="3cdb2-128">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3cdb2-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="3cdb2-129">檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3cdb2-129">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="3cdb2-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="3cdb2-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
