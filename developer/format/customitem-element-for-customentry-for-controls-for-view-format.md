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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855604"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="4c9e1-102">檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4c9e1-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="4c9e1-103">定義控制項所顯示的資料和顯示方式。</span><span class="sxs-lookup"><span data-stu-id="4c9e1-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="4c9e1-104">定義可供檢視的控制項時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="4c9e1-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="4c9e1-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目CustomControl CustomEntries CustomEntry 用於檢視 （格式） 的控制項的檢視 （格式） CustomItem 元素的控制項的檢視 （格式） CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="4c9e1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4c9e1-106">語法</span><span class="sxs-lookup"><span data-stu-id="4c9e1-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4c9e1-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="4c9e1-107">Attributes and Elements</span></span>

<span data-ttu-id="4c9e1-108">下列各節說明屬性、 子項目和父項目`CustomItem`項目。</span><span class="sxs-lookup"><span data-stu-id="4c9e1-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="4c9e1-109">如需詳細資訊，請參閱 < 備註 >。</span><span class="sxs-lookup"><span data-stu-id="4c9e1-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="4c9e1-110">屬性</span><span class="sxs-lookup"><span data-stu-id="4c9e1-110">Attributes</span></span>

<span data-ttu-id="4c9e1-111">無。</span><span class="sxs-lookup"><span data-stu-id="4c9e1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4c9e1-112">子元素</span><span class="sxs-lookup"><span data-stu-id="4c9e1-112">Child Elements</span></span>

|<span data-ttu-id="4c9e1-113">元素</span><span class="sxs-lookup"><span data-stu-id="4c9e1-113">Element</span></span>|<span data-ttu-id="4c9e1-114">描述</span><span class="sxs-lookup"><span data-stu-id="4c9e1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4c9e1-115">ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="4c9e1-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="4c9e1-116">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="4c9e1-116">Optional element.</span></span><br /><br /> <span data-ttu-id="4c9e1-117">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="4c9e1-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="4c9e1-118">用於檢視 （格式） 的控制項 CustomItem 的框架項目</span><span class="sxs-lookup"><span data-stu-id="4c9e1-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="4c9e1-119">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="4c9e1-119">Optional element.</span></span><br /><br /> <span data-ttu-id="4c9e1-120">定義資料的顯示方式，例如將資料轉移至左邊或右邊。</span><span class="sxs-lookup"><span data-stu-id="4c9e1-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="4c9e1-121">CustomItem 控制項的檢視 （格式） 的新行項目</span><span class="sxs-lookup"><span data-stu-id="4c9e1-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="4c9e1-122">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="4c9e1-122">Optional element.</span></span><br /><br /> <span data-ttu-id="4c9e1-123">將控制項的顯示中的空白行。</span><span class="sxs-lookup"><span data-stu-id="4c9e1-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="4c9e1-124">CustomItem 用於檢視 （格式） 的控制項的文字項目</span><span class="sxs-lookup"><span data-stu-id="4c9e1-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="4c9e1-125">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="4c9e1-125">Optional element.</span></span><br /><br /> <span data-ttu-id="4c9e1-126">將控制項的顯示文字，例如括號或括號。</span><span class="sxs-lookup"><span data-stu-id="4c9e1-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4c9e1-127">父元素</span><span class="sxs-lookup"><span data-stu-id="4c9e1-127">Parent Elements</span></span>

|<span data-ttu-id="4c9e1-128">元素</span><span class="sxs-lookup"><span data-stu-id="4c9e1-128">Element</span></span>|<span data-ttu-id="4c9e1-129">描述</span><span class="sxs-lookup"><span data-stu-id="4c9e1-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4c9e1-130">用於檢視 （格式） 的控制項 CustomEntries CustomEntry 項目</span><span class="sxs-lookup"><span data-stu-id="4c9e1-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="4c9e1-131">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="4c9e1-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4c9e1-132">備註</span><span class="sxs-lookup"><span data-stu-id="4c9e1-132">Remarks</span></span>

<span data-ttu-id="4c9e1-133">當指定的子項目`CustomItem`項目，請記住下列：</span><span class="sxs-lookup"><span data-stu-id="4c9e1-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="4c9e1-134">必須依照以下順序新增子項目： `ExpressionBinding`， `NewLine`， `Text`，和`Frame`。</span><span class="sxs-lookup"><span data-stu-id="4c9e1-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="4c9e1-135">，您可以指定序列的數目沒有上限限制。</span><span class="sxs-lookup"><span data-stu-id="4c9e1-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="4c9e1-136">在每個序列中，沒有任何數目的最大限制`ExpressionBinding`您可以使用的項目。</span><span class="sxs-lookup"><span data-stu-id="4c9e1-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c9e1-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c9e1-137">See Also</span></span>

[<span data-ttu-id="4c9e1-138">ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="4c9e1-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="4c9e1-139">用於檢視 （格式） 的控制項 CustomItem 的框架項目</span><span class="sxs-lookup"><span data-stu-id="4c9e1-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="4c9e1-140">CustomItem 控制項的檢視 （格式） 的新行項目</span><span class="sxs-lookup"><span data-stu-id="4c9e1-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="4c9e1-141">CustomItem 用於檢視 （格式） 的控制項的文字項目</span><span class="sxs-lookup"><span data-stu-id="4c9e1-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="4c9e1-142">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="4c9e1-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
