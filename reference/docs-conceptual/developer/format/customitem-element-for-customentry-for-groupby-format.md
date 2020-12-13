---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)
description: GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)
ms.openlocfilehash: 5db23ad4dad5bd66ea64b9c6e91b8224a4aa4eca
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645975"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="e5e74-103">GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e5e74-103">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="e5e74-104">定義自訂控制項視圖所顯示的資料，以及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="e5e74-104">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="e5e74-105">定義如何顯示新的物件群組時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="e5e74-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e5e74-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy (格式) CustomEntries 元素適用于 groupby (格式) CustomItem 專案用於 CustomEntry 的 GroupBy (格式) </span><span class="sxs-lookup"><span data-stu-id="e5e74-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5e74-107">語法</span><span class="sxs-lookup"><span data-stu-id="e5e74-107">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5e74-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e5e74-108">Attributes and Elements</span></span>

<span data-ttu-id="e5e74-109">下列各節說明屬性、子專案和元素的父元素 `CustomItem` 。</span><span class="sxs-lookup"><span data-stu-id="e5e74-109">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5e74-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e5e74-110">Attributes</span></span>

<span data-ttu-id="e5e74-111">無。</span><span class="sxs-lookup"><span data-stu-id="e5e74-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5e74-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e5e74-112">Child Elements</span></span>

|<span data-ttu-id="e5e74-113">元素</span><span class="sxs-lookup"><span data-stu-id="e5e74-113">Element</span></span>|<span data-ttu-id="e5e74-114">描述</span><span class="sxs-lookup"><span data-stu-id="e5e74-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5e74-115">GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e5e74-115">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="e5e74-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e5e74-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e5e74-117">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="e5e74-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="e5e74-118">GroupBy 之 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e5e74-118">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="e5e74-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e5e74-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e5e74-120">定義自訂控制項視圖所顯示的資料，以及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="e5e74-120">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="e5e74-121">GroupBy 之 CustomItem 的 NewLine 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e5e74-121">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="e5e74-122">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e5e74-122">Optional element.</span></span><br /><br /> <span data-ttu-id="e5e74-123">在控制項的顯示中加入空白行。</span><span class="sxs-lookup"><span data-stu-id="e5e74-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="e5e74-124">GroupBy 之 CustomItem 的文字元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e5e74-124">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="e5e74-125">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e5e74-125">Optional element.</span></span><br /><br /> <span data-ttu-id="e5e74-126">指定控制項所顯示之資料的其他文字。</span><span class="sxs-lookup"><span data-stu-id="e5e74-126">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e5e74-127">父項目</span><span class="sxs-lookup"><span data-stu-id="e5e74-127">Parent Elements</span></span>

|<span data-ttu-id="e5e74-128">元素</span><span class="sxs-lookup"><span data-stu-id="e5e74-128">Element</span></span>|<span data-ttu-id="e5e74-129">描述</span><span class="sxs-lookup"><span data-stu-id="e5e74-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5e74-130">GroupBy 之 CustomControl 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e5e74-130">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="e5e74-131">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="e5e74-131">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e5e74-132">備註</span><span class="sxs-lookup"><span data-stu-id="e5e74-132">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="e5e74-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5e74-133">See Also</span></span>

[<span data-ttu-id="e5e74-134">GroupBy 之 CustomControl 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e5e74-134">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="e5e74-135">GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e5e74-135">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="e5e74-136">GroupBy 之 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e5e74-136">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="e5e74-137">GroupBy 之 CustomItem 的 NewLine 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e5e74-137">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="e5e74-138">GroupBy 之 CustomItem 的文字元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e5e74-138">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="e5e74-139">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="e5e74-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
