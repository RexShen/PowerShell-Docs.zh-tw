---
title: 用於檢視 （格式） 的控制項 CustomEntry CustomItem 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066374"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="ebf7e-102">檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ebf7e-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="ebf7e-103">定義控制項所顯示的資料和顯示方式。</span><span class="sxs-lookup"><span data-stu-id="ebf7e-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="ebf7e-104">定義可供檢視的控制項時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="ebf7e-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="ebf7e-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目CustomControl CustomEntries CustomEntry 用於檢視 （格式） 的控制項的檢視 （格式） CustomItem 元素的控制項的檢視 （格式） CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="ebf7e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ebf7e-106">語法</span><span class="sxs-lookup"><span data-stu-id="ebf7e-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ebf7e-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ebf7e-107">Attributes and Elements</span></span>

<span data-ttu-id="ebf7e-108">下列各節說明屬性、 子項目和父項目`CustomItem`項目。</span><span class="sxs-lookup"><span data-stu-id="ebf7e-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="ebf7e-109">如需詳細資訊，請參閱 < 備註 >。</span><span class="sxs-lookup"><span data-stu-id="ebf7e-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="ebf7e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="ebf7e-110">Attributes</span></span>

<span data-ttu-id="ebf7e-111">無。</span><span class="sxs-lookup"><span data-stu-id="ebf7e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ebf7e-112">子元素</span><span class="sxs-lookup"><span data-stu-id="ebf7e-112">Child Elements</span></span>

|<span data-ttu-id="ebf7e-113">元素</span><span class="sxs-lookup"><span data-stu-id="ebf7e-113">Element</span></span>|<span data-ttu-id="ebf7e-114">描述</span><span class="sxs-lookup"><span data-stu-id="ebf7e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ebf7e-115">ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="ebf7e-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="ebf7e-116">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="ebf7e-116">Optional element.</span></span><br /><br /> <span data-ttu-id="ebf7e-117">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="ebf7e-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="ebf7e-118">用於檢視 （格式） 的控制項 CustomItem 的框架項目</span><span class="sxs-lookup"><span data-stu-id="ebf7e-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="ebf7e-119">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="ebf7e-119">Optional element.</span></span><br /><br /> <span data-ttu-id="ebf7e-120">定義資料的顯示方式，例如將資料轉移至左邊或右邊。</span><span class="sxs-lookup"><span data-stu-id="ebf7e-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="ebf7e-121">CustomItem 控制項的檢視 （格式） 的新行項目</span><span class="sxs-lookup"><span data-stu-id="ebf7e-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="ebf7e-122">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="ebf7e-122">Optional element.</span></span><br /><br /> <span data-ttu-id="ebf7e-123">將控制項的顯示中的空白行。</span><span class="sxs-lookup"><span data-stu-id="ebf7e-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="ebf7e-124">CustomItem 用於檢視 （格式） 的控制項的文字項目</span><span class="sxs-lookup"><span data-stu-id="ebf7e-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="ebf7e-125">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="ebf7e-125">Optional element.</span></span><br /><br /> <span data-ttu-id="ebf7e-126">將控制項的顯示文字，例如括號或括號。</span><span class="sxs-lookup"><span data-stu-id="ebf7e-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ebf7e-127">父項目</span><span class="sxs-lookup"><span data-stu-id="ebf7e-127">Parent Elements</span></span>

|<span data-ttu-id="ebf7e-128">項目</span><span class="sxs-lookup"><span data-stu-id="ebf7e-128">Element</span></span>|<span data-ttu-id="ebf7e-129">描述</span><span class="sxs-lookup"><span data-stu-id="ebf7e-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ebf7e-130">用於檢視 （格式） 的控制項 CustomEntries CustomEntry 項目</span><span class="sxs-lookup"><span data-stu-id="ebf7e-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="ebf7e-131">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="ebf7e-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ebf7e-132">備註</span><span class="sxs-lookup"><span data-stu-id="ebf7e-132">Remarks</span></span>

<span data-ttu-id="ebf7e-133">當指定的子項目`CustomItem`項目，請記住下列：</span><span class="sxs-lookup"><span data-stu-id="ebf7e-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="ebf7e-134">必須依照以下順序新增子項目： `ExpressionBinding`， `NewLine`， `Text`，和`Frame`。</span><span class="sxs-lookup"><span data-stu-id="ebf7e-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="ebf7e-135">，您可以指定序列的數目沒有上限限制。</span><span class="sxs-lookup"><span data-stu-id="ebf7e-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="ebf7e-136">在每個序列中，沒有任何數目的最大限制`ExpressionBinding`您可以使用的項目。</span><span class="sxs-lookup"><span data-stu-id="ebf7e-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="ebf7e-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebf7e-137">See Also</span></span>

[<span data-ttu-id="ebf7e-138">ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="ebf7e-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="ebf7e-139">用於檢視 （格式） 的控制項 CustomItem 的框架項目</span><span class="sxs-lookup"><span data-stu-id="ebf7e-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="ebf7e-140">CustomItem 控制項的檢視 （格式） 的新行項目</span><span class="sxs-lookup"><span data-stu-id="ebf7e-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="ebf7e-141">CustomItem 用於檢視 （格式） 的控制項的文字項目</span><span class="sxs-lookup"><span data-stu-id="ebf7e-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="ebf7e-142">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="ebf7e-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
