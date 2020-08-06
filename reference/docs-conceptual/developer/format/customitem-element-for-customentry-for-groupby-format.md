---
title: 適用于 CustomEntry 之 GroupBy (格式的 CustomItem 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e8086c5330b6644f83316ad4ae33c33ba40d9eee
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783716"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="e9e63-102">GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e9e63-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="e9e63-103">定義自訂控制項視圖顯示的資料，以及顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="e9e63-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="e9e63-104">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="e9e63-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e9e63-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素（groupby (格式）) CustomEntries 元素（適用于 groupby (格式的 CustomItem) CustomEntry 元素） (</span><span class="sxs-lookup"><span data-stu-id="e9e63-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e9e63-106">語法</span><span class="sxs-lookup"><span data-stu-id="e9e63-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e9e63-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e9e63-107">Attributes and Elements</span></span>

<span data-ttu-id="e9e63-108">下列各節說明屬性、子專案和元素的父元素 `CustomItem` 。</span><span class="sxs-lookup"><span data-stu-id="e9e63-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e9e63-109">屬性</span><span class="sxs-lookup"><span data-stu-id="e9e63-109">Attributes</span></span>

<span data-ttu-id="e9e63-110">無。</span><span class="sxs-lookup"><span data-stu-id="e9e63-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e9e63-111">子元素</span><span class="sxs-lookup"><span data-stu-id="e9e63-111">Child Elements</span></span>

|<span data-ttu-id="e9e63-112">元素</span><span class="sxs-lookup"><span data-stu-id="e9e63-112">Element</span></span>|<span data-ttu-id="e9e63-113">描述</span><span class="sxs-lookup"><span data-stu-id="e9e63-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e9e63-114">GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e9e63-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="e9e63-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e9e63-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e9e63-116">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="e9e63-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="e9e63-117">GroupBy 之 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e9e63-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="e9e63-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e9e63-118">Optional element.</span></span><br /><br /> <span data-ttu-id="e9e63-119">定義自訂控制項視圖顯示的資料，以及顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="e9e63-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="e9e63-120">GroupBy 之 CustomItem 的 NewLine 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e9e63-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="e9e63-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e9e63-121">Optional element.</span></span><br /><br /> <span data-ttu-id="e9e63-122">將空白行加入控制項的顯示中。</span><span class="sxs-lookup"><span data-stu-id="e9e63-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="e9e63-123">GroupBy 之 CustomItem 的文字元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e9e63-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="e9e63-124">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e9e63-124">Optional element.</span></span><br /><br /> <span data-ttu-id="e9e63-125">指定控制項所顯示之資料的其他文字。</span><span class="sxs-lookup"><span data-stu-id="e9e63-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e9e63-126">父項目</span><span class="sxs-lookup"><span data-stu-id="e9e63-126">Parent Elements</span></span>

|<span data-ttu-id="e9e63-127">元素</span><span class="sxs-lookup"><span data-stu-id="e9e63-127">Element</span></span>|<span data-ttu-id="e9e63-128">描述</span><span class="sxs-lookup"><span data-stu-id="e9e63-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e9e63-129">GroupBy 之 CustomControl 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e9e63-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="e9e63-130">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="e9e63-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e9e63-131">備註</span><span class="sxs-lookup"><span data-stu-id="e9e63-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="e9e63-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9e63-132">See Also</span></span>

[<span data-ttu-id="e9e63-133">GroupBy 之 CustomControl 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e9e63-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="e9e63-134">GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e9e63-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="e9e63-135">GroupBy 之 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e9e63-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="e9e63-136">GroupBy 之 CustomItem 的 NewLine 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e9e63-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="e9e63-137">GroupBy 之 CustomItem 的文字元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e9e63-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="e9e63-138">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="e9e63-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
