---
title: GroupBy 之 CustomEntry 的 CustomItem 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363877"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="80e8e-102">GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="80e8e-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="80e8e-103">定義自訂控制項視圖顯示的資料，以及顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="80e8e-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="80e8e-104">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="80e8e-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="80e8e-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（format） CustomEntries 專案的 groupby （format） CustomControl 元素，適用于的 CustomControl for GroupBy （format） CustomItem 元素GroupBy 的 CustomEntry （格式）</span><span class="sxs-lookup"><span data-stu-id="80e8e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="80e8e-106">語法</span><span class="sxs-lookup"><span data-stu-id="80e8e-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="80e8e-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="80e8e-107">Attributes and Elements</span></span>

<span data-ttu-id="80e8e-108">下列各節說明屬性、子專案，以及 `CustomItem` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="80e8e-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="80e8e-109">屬性</span><span class="sxs-lookup"><span data-stu-id="80e8e-109">Attributes</span></span>

<span data-ttu-id="80e8e-110">無。</span><span class="sxs-lookup"><span data-stu-id="80e8e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="80e8e-111">子元素</span><span class="sxs-lookup"><span data-stu-id="80e8e-111">Child Elements</span></span>

|<span data-ttu-id="80e8e-112">元素</span><span class="sxs-lookup"><span data-stu-id="80e8e-112">Element</span></span>|<span data-ttu-id="80e8e-113">描述</span><span class="sxs-lookup"><span data-stu-id="80e8e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80e8e-114">GroupBy 之 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="80e8e-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="80e8e-115">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="80e8e-115">Optional element.</span></span><br /><br /> <span data-ttu-id="80e8e-116">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="80e8e-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="80e8e-117">GroupBy 之 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="80e8e-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="80e8e-118">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="80e8e-118">Optional element.</span></span><br /><br /> <span data-ttu-id="80e8e-119">定義自訂控制項視圖顯示的資料，以及顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="80e8e-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="80e8e-120">GroupBy 的 CustomItem 的分行符號元素（格式）</span><span class="sxs-lookup"><span data-stu-id="80e8e-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="80e8e-121">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="80e8e-121">Optional element.</span></span><br /><br /> <span data-ttu-id="80e8e-122">將空白行加入控制項的顯示中。</span><span class="sxs-lookup"><span data-stu-id="80e8e-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="80e8e-123">GroupBy 的 CustomItem 的文字元素（格式）</span><span class="sxs-lookup"><span data-stu-id="80e8e-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="80e8e-124">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="80e8e-124">Optional element.</span></span><br /><br /> <span data-ttu-id="80e8e-125">指定控制項所顯示之資料的其他文字。</span><span class="sxs-lookup"><span data-stu-id="80e8e-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="80e8e-126">父元素</span><span class="sxs-lookup"><span data-stu-id="80e8e-126">Parent Elements</span></span>

|<span data-ttu-id="80e8e-127">元素</span><span class="sxs-lookup"><span data-stu-id="80e8e-127">Element</span></span>|<span data-ttu-id="80e8e-128">描述</span><span class="sxs-lookup"><span data-stu-id="80e8e-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80e8e-129">GroupBy 之 CustomControl 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="80e8e-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="80e8e-130">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="80e8e-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="80e8e-131">備註</span><span class="sxs-lookup"><span data-stu-id="80e8e-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="80e8e-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80e8e-132">See Also</span></span>

[<span data-ttu-id="80e8e-133">GroupBy 之 CustomControl 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="80e8e-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="80e8e-134">GroupBy 之 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="80e8e-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="80e8e-135">GroupBy 之 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="80e8e-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="80e8e-136">GroupBy 的 CustomItem 的分行符號元素（格式）</span><span class="sxs-lookup"><span data-stu-id="80e8e-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="80e8e-137">GroupBy 的 CustomItem 的文字元素（格式）</span><span class="sxs-lookup"><span data-stu-id="80e8e-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="80e8e-138">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="80e8e-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
