---
title: 設定之控制項的 CustomEntry 的 CustomItem 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364027"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="89e71-102">設定之控制項的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="89e71-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="89e71-103">定義控制項所顯示的資料及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="89e71-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="89e71-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="89e71-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="89e71-105">Configuration 元素（格式）控制設定（format） CustomControl 元素的設定（格式）控制項專案的設定專案（格式） CustomControl 設定的 CustomEntries 元素（格式）Format） CustomEntry 元素，用於 CustomControl 控制項的設定（Format） CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="89e71-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="89e71-106">語法</span><span class="sxs-lookup"><span data-stu-id="89e71-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="89e71-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="89e71-107">Attributes and Elements</span></span>

<span data-ttu-id="89e71-108">下列各節說明屬性、子專案，以及 `CustomItem` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="89e71-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="89e71-109">如需詳細資訊，請參閱備註。</span><span class="sxs-lookup"><span data-stu-id="89e71-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="89e71-110">屬性</span><span class="sxs-lookup"><span data-stu-id="89e71-110">Attributes</span></span>

<span data-ttu-id="89e71-111">無。</span><span class="sxs-lookup"><span data-stu-id="89e71-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="89e71-112">子元素</span><span class="sxs-lookup"><span data-stu-id="89e71-112">Child Elements</span></span>

|<span data-ttu-id="89e71-113">元素</span><span class="sxs-lookup"><span data-stu-id="89e71-113">Element</span></span>|<span data-ttu-id="89e71-114">描述</span><span class="sxs-lookup"><span data-stu-id="89e71-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="89e71-115">設定之控制項的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="89e71-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="89e71-116">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="89e71-116">Optional element.</span></span><br /><br /> <span data-ttu-id="89e71-117">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="89e71-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="89e71-118">用於設定之控制項的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="89e71-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="89e71-119">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="89e71-119">Optional element.</span></span><br /><br /> <span data-ttu-id="89e71-120">定義資料的顯示方式，例如將資料向左或向右移位。</span><span class="sxs-lookup"><span data-stu-id="89e71-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="89e71-121">設定之控制項的 CustomItem 的新行元素（格式）</span><span class="sxs-lookup"><span data-stu-id="89e71-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="89e71-122">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="89e71-122">Optional element.</span></span><br /><br /> <span data-ttu-id="89e71-123">將空白行加入控制項的顯示中。</span><span class="sxs-lookup"><span data-stu-id="89e71-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="89e71-124">設定之控制項的 CustomItem 的文字元素（格式）</span><span class="sxs-lookup"><span data-stu-id="89e71-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="89e71-125">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="89e71-125">Optional element.</span></span><br /><br /> <span data-ttu-id="89e71-126">將文字（例如括弧或括弧）新增至控制項的顯示。</span><span class="sxs-lookup"><span data-stu-id="89e71-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="89e71-127">父元素</span><span class="sxs-lookup"><span data-stu-id="89e71-127">Parent Elements</span></span>

|<span data-ttu-id="89e71-128">元素</span><span class="sxs-lookup"><span data-stu-id="89e71-128">Element</span></span>|<span data-ttu-id="89e71-129">描述</span><span class="sxs-lookup"><span data-stu-id="89e71-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="89e71-130">設定之控制項的 CustomControl 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="89e71-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="89e71-131">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="89e71-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="89e71-132">備註</span><span class="sxs-lookup"><span data-stu-id="89e71-132">Remarks</span></span>

<span data-ttu-id="89e71-133">指定 `CustomItem` 元素的子項目時，請記住下列事項：</span><span class="sxs-lookup"><span data-stu-id="89e71-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="89e71-134">子項目必須以下列順序加入： `ExpressionBinding`、`NewLine`、`Text` 和 `Frame`。</span><span class="sxs-lookup"><span data-stu-id="89e71-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="89e71-135">您可以指定的序列數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="89e71-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="89e71-136">在每個序列中，您可以使用的 @no__t 0 元素數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="89e71-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="89e71-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89e71-137">See Also</span></span>

[<span data-ttu-id="89e71-138">設定之控制項的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="89e71-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="89e71-139">用於設定之控制項的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="89e71-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="89e71-140">設定之控制項的 CustomItem 的新行元素（格式）</span><span class="sxs-lookup"><span data-stu-id="89e71-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="89e71-141">設定之控制項的 CustomItem 的文字元素（格式）</span><span class="sxs-lookup"><span data-stu-id="89e71-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="89e71-142">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="89e71-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
