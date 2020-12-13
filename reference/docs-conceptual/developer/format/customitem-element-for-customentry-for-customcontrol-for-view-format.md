---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之 CustomControl 的 CustomEntry 的 CustomItem 元素 (格式)
description: 檢視之 CustomControl 的 CustomEntry 的 CustomItem 元素 (格式)
ms.openlocfilehash: 9090a3ada5316ba5ddb4a9c46eee37c11982ae6e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666734"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="70a35-103">檢視之 CustomControl 的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="70a35-103">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="70a35-104">定義自訂控制項視圖所顯示的資料，以及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="70a35-104">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="70a35-105">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="70a35-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="70a35-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 專案 (格式) CustomEntries 專案 (格式) 專案 (格式) CustomEntry 專案 (格式) CustomEntries 專案格式 CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="70a35-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="70a35-107">語法</span><span class="sxs-lookup"><span data-stu-id="70a35-107">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="70a35-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="70a35-108">Attributes and Elements</span></span>

<span data-ttu-id="70a35-109">下列各節說明屬性、子專案和元素的父元素 `CustomItem` 。</span><span class="sxs-lookup"><span data-stu-id="70a35-109">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="70a35-110">屬性</span><span class="sxs-lookup"><span data-stu-id="70a35-110">Attributes</span></span>

<span data-ttu-id="70a35-111">無。</span><span class="sxs-lookup"><span data-stu-id="70a35-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="70a35-112">子元素</span><span class="sxs-lookup"><span data-stu-id="70a35-112">Child Elements</span></span>

|<span data-ttu-id="70a35-113">元素</span><span class="sxs-lookup"><span data-stu-id="70a35-113">Element</span></span>|<span data-ttu-id="70a35-114">描述</span><span class="sxs-lookup"><span data-stu-id="70a35-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70a35-115">檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="70a35-115">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="70a35-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="70a35-116">Optional element.</span></span><br /><br /> <span data-ttu-id="70a35-117">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="70a35-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="70a35-118">檢視之 CustomControl 的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="70a35-118">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="70a35-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="70a35-119">Optional element.</span></span><br /><br /> <span data-ttu-id="70a35-120">定義自訂控制項視圖所顯示的資料，以及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="70a35-120">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="70a35-121">適用于 View (格式之自訂控制項的 CustomItem 的分行符號元素) </span><span class="sxs-lookup"><span data-stu-id="70a35-121">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="70a35-122">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="70a35-122">Optional element.</span></span><br /><br /> <span data-ttu-id="70a35-123">在控制項的顯示中加入空白行。</span><span class="sxs-lookup"><span data-stu-id="70a35-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="70a35-124">CustomItem for CustomControl for View (Format 的 Text 元素) </span><span class="sxs-lookup"><span data-stu-id="70a35-124">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="70a35-125">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="70a35-125">Optional element.</span></span><br /><br /> <span data-ttu-id="70a35-126">指定控制項所顯示之資料的其他文字。</span><span class="sxs-lookup"><span data-stu-id="70a35-126">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="70a35-127">父項目</span><span class="sxs-lookup"><span data-stu-id="70a35-127">Parent Elements</span></span>

|<span data-ttu-id="70a35-128">元素</span><span class="sxs-lookup"><span data-stu-id="70a35-128">Element</span></span>|<span data-ttu-id="70a35-129">描述</span><span class="sxs-lookup"><span data-stu-id="70a35-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70a35-130">檢視之 CustomControl 的 CustomEntries 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="70a35-130">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="70a35-131">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="70a35-131">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="70a35-132">備註</span><span class="sxs-lookup"><span data-stu-id="70a35-132">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="70a35-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70a35-133">See Also</span></span>

[<span data-ttu-id="70a35-134">適用于 CustomEntries 的 CustomEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="70a35-134">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="70a35-135">檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="70a35-135">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="70a35-136">檢視之 CustomControl 的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="70a35-136">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="70a35-137">檢視之 CustomControl 的 CustomItem 的 NewLine 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="70a35-137">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="70a35-138">CustomItem for CustomControl for View (Format 的 Text 元素) </span><span class="sxs-lookup"><span data-stu-id="70a35-138">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="70a35-139">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="70a35-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
