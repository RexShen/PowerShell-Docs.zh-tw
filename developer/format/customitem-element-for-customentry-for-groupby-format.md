---
title: GroupBy （格式） 的 CustomEntry CustomItem 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066390"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="bc523-102">GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bc523-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="bc523-103">定義自訂的控制項檢視所顯示的資料和顯示方式。</span><span class="sxs-lookup"><span data-stu-id="bc523-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="bc523-104">定義新的群組物件的顯示方式時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="bc523-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="bc523-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomItem 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素GroupBy （格式） 的 CustomEntry</span><span class="sxs-lookup"><span data-stu-id="bc523-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bc523-106">語法</span><span class="sxs-lookup"><span data-stu-id="bc523-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bc523-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bc523-107">Attributes and Elements</span></span>

<span data-ttu-id="bc523-108">下列各節說明屬性、 子項目和父項目`CustomItem`項目。</span><span class="sxs-lookup"><span data-stu-id="bc523-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bc523-109">屬性</span><span class="sxs-lookup"><span data-stu-id="bc523-109">Attributes</span></span>

<span data-ttu-id="bc523-110">無。</span><span class="sxs-lookup"><span data-stu-id="bc523-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bc523-111">子元素</span><span class="sxs-lookup"><span data-stu-id="bc523-111">Child Elements</span></span>

|<span data-ttu-id="bc523-112">元素</span><span class="sxs-lookup"><span data-stu-id="bc523-112">Element</span></span>|<span data-ttu-id="bc523-113">描述</span><span class="sxs-lookup"><span data-stu-id="bc523-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc523-114">ExpressionBinding CustomItem 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="bc523-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="bc523-115">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="bc523-115">Optional element.</span></span><br /><br /> <span data-ttu-id="bc523-116">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="bc523-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="bc523-117">GroupBy （格式） 的 CustomItem 的框架項目</span><span class="sxs-lookup"><span data-stu-id="bc523-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="bc523-118">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="bc523-118">Optional element.</span></span><br /><br /> <span data-ttu-id="bc523-119">定義自訂的控制項檢視所顯示的資料和顯示方式。</span><span class="sxs-lookup"><span data-stu-id="bc523-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="bc523-120">CustomItem 的 GroupBy （格式） 的新行項目</span><span class="sxs-lookup"><span data-stu-id="bc523-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="bc523-121">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="bc523-121">Optional element.</span></span><br /><br /> <span data-ttu-id="bc523-122">將控制項的顯示中的空白行。</span><span class="sxs-lookup"><span data-stu-id="bc523-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="bc523-123">GroupBy （格式） 的 CustomItem 的文字項目</span><span class="sxs-lookup"><span data-stu-id="bc523-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="bc523-124">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="bc523-124">Optional element.</span></span><br /><br /> <span data-ttu-id="bc523-125">指定要由控制項所顯示的資料的其他文字。</span><span class="sxs-lookup"><span data-stu-id="bc523-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bc523-126">父項目</span><span class="sxs-lookup"><span data-stu-id="bc523-126">Parent Elements</span></span>

|<span data-ttu-id="bc523-127">項目</span><span class="sxs-lookup"><span data-stu-id="bc523-127">Element</span></span>|<span data-ttu-id="bc523-128">描述</span><span class="sxs-lookup"><span data-stu-id="bc523-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc523-129">GroupBy （格式） 的 CustomControl CustomEntry 項目</span><span class="sxs-lookup"><span data-stu-id="bc523-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="bc523-130">提供自訂的控制項檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="bc523-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bc523-131">備註</span><span class="sxs-lookup"><span data-stu-id="bc523-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="bc523-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc523-132">See Also</span></span>

[<span data-ttu-id="bc523-133">GroupBy （格式） 的 CustomControl CustomEntry 項目</span><span class="sxs-lookup"><span data-stu-id="bc523-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="bc523-134">ExpressionBinding CustomItem 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="bc523-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="bc523-135">GroupBy （格式） 的 CustomItem 的框架項目</span><span class="sxs-lookup"><span data-stu-id="bc523-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="bc523-136">CustomItem 的 GroupBy （格式） 的新行項目</span><span class="sxs-lookup"><span data-stu-id="bc523-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="bc523-137">GroupBy （格式） 的 CustomItem 的文字項目</span><span class="sxs-lookup"><span data-stu-id="bc523-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="bc523-138">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="bc523-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
