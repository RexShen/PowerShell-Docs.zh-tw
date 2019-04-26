---
title: CustomItem CustomEntry 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066425"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="5d610-102">設定之控制項的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5d610-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="5d610-103">定義控制項所顯示的資料和顯示方式。</span><span class="sxs-lookup"><span data-stu-id="5d610-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="5d610-104">定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="5d610-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="5d610-105">組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目CustomControl CustomEntry 控制項組態的組態 （格式） CustomItem 元素的控制項的格式） CustomEntry 項目</span><span class="sxs-lookup"><span data-stu-id="5d610-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="5d610-106">語法</span><span class="sxs-lookup"><span data-stu-id="5d610-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5d610-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5d610-107">Attributes and Elements</span></span>

<span data-ttu-id="5d610-108">下列各節說明屬性、 子項目和父項目`CustomItem`項目。</span><span class="sxs-lookup"><span data-stu-id="5d610-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="5d610-109">如需詳細資訊，請參閱 < 備註 >。</span><span class="sxs-lookup"><span data-stu-id="5d610-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="5d610-110">屬性</span><span class="sxs-lookup"><span data-stu-id="5d610-110">Attributes</span></span>

<span data-ttu-id="5d610-111">無。</span><span class="sxs-lookup"><span data-stu-id="5d610-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5d610-112">子元素</span><span class="sxs-lookup"><span data-stu-id="5d610-112">Child Elements</span></span>

|<span data-ttu-id="5d610-113">元素</span><span class="sxs-lookup"><span data-stu-id="5d610-113">Element</span></span>|<span data-ttu-id="5d610-114">描述</span><span class="sxs-lookup"><span data-stu-id="5d610-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5d610-115">ExpressionBinding CustomItem 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="5d610-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="5d610-116">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="5d610-116">Optional element.</span></span><br /><br /> <span data-ttu-id="5d610-117">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="5d610-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="5d610-118">CustomItem 組態 （格式） 的控制項的框架項目</span><span class="sxs-lookup"><span data-stu-id="5d610-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="5d610-119">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="5d610-119">Optional element.</span></span><br /><br /> <span data-ttu-id="5d610-120">定義資料的顯示方式，例如將資料轉移至左邊或右邊。</span><span class="sxs-lookup"><span data-stu-id="5d610-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="5d610-121">CustomItem 組態 （格式） 的控制項的新行項目</span><span class="sxs-lookup"><span data-stu-id="5d610-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="5d610-122">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="5d610-122">Optional element.</span></span><br /><br /> <span data-ttu-id="5d610-123">將控制項的顯示中的空白行。</span><span class="sxs-lookup"><span data-stu-id="5d610-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="5d610-124">CustomItem 組態 （格式） 的控制項的文字項目</span><span class="sxs-lookup"><span data-stu-id="5d610-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="5d610-125">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="5d610-125">Optional element.</span></span><br /><br /> <span data-ttu-id="5d610-126">將控制項的顯示文字，例如括號或括號。</span><span class="sxs-lookup"><span data-stu-id="5d610-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5d610-127">父項目</span><span class="sxs-lookup"><span data-stu-id="5d610-127">Parent Elements</span></span>

|<span data-ttu-id="5d610-128">項目</span><span class="sxs-lookup"><span data-stu-id="5d610-128">Element</span></span>|<span data-ttu-id="5d610-129">描述</span><span class="sxs-lookup"><span data-stu-id="5d610-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5d610-130">CustomEntry CustomControl 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="5d610-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="5d610-131">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="5d610-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5d610-132">備註</span><span class="sxs-lookup"><span data-stu-id="5d610-132">Remarks</span></span>

<span data-ttu-id="5d610-133">當指定的子項目`CustomItem`項目，請記住下列：</span><span class="sxs-lookup"><span data-stu-id="5d610-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="5d610-134">必須依照以下順序新增子項目： `ExpressionBinding`， `NewLine`， `Text`，和`Frame`。</span><span class="sxs-lookup"><span data-stu-id="5d610-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="5d610-135">，您可以指定序列的數目沒有上限限制。</span><span class="sxs-lookup"><span data-stu-id="5d610-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="5d610-136">在每個序列中，沒有任何數目的最大限制`ExpressionBinding`您可以使用的項目。</span><span class="sxs-lookup"><span data-stu-id="5d610-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d610-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d610-137">See Also</span></span>

[<span data-ttu-id="5d610-138">ExpressionBinding CustomItem 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="5d610-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="5d610-139">CustomItem 組態 （格式） 的控制項的框架項目</span><span class="sxs-lookup"><span data-stu-id="5d610-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="5d610-140">CustomItem 組態 （格式） 的控制項的新行項目</span><span class="sxs-lookup"><span data-stu-id="5d610-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="5d610-141">CustomItem 組態 （格式） 的控制項的文字項目</span><span class="sxs-lookup"><span data-stu-id="5d610-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="5d610-142">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="5d610-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
