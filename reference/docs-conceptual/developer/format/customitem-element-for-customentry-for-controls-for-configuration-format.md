---
title: CustomEntry 之控制項的 CustomItem 元素，用於設定 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: bb8124242496f192717127f201674bc1428e5de0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785858"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="62d46-102">設定之控制項的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="62d46-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="62d46-103">定義控制項所顯示的資料及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="62d46-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="62d46-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="62d46-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="62d46-105">Configuration 專案 (格式) Controls 設定的控制項元素 (格式設定的控制項) 控制項專案 (格式) 設定 (格式的 CustomControl 的 CustomControl 元素 CustomControl 的設定) 格式 (CustomItem 元素適用于設定的控制項的 CustomEntry 的 CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="62d46-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="62d46-106">語法</span><span class="sxs-lookup"><span data-stu-id="62d46-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="62d46-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="62d46-107">Attributes and Elements</span></span>

<span data-ttu-id="62d46-108">下列各節說明屬性、子專案和元素的父元素 `CustomItem` 。</span><span class="sxs-lookup"><span data-stu-id="62d46-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="62d46-109">如需詳細資訊，請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="62d46-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="62d46-110">屬性</span><span class="sxs-lookup"><span data-stu-id="62d46-110">Attributes</span></span>

<span data-ttu-id="62d46-111">無。</span><span class="sxs-lookup"><span data-stu-id="62d46-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="62d46-112">子元素</span><span class="sxs-lookup"><span data-stu-id="62d46-112">Child Elements</span></span>

|<span data-ttu-id="62d46-113">元素</span><span class="sxs-lookup"><span data-stu-id="62d46-113">Element</span></span>|<span data-ttu-id="62d46-114">描述</span><span class="sxs-lookup"><span data-stu-id="62d46-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="62d46-115">設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="62d46-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="62d46-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="62d46-116">Optional element.</span></span><br /><br /> <span data-ttu-id="62d46-117">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="62d46-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="62d46-118">設定之控制項的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="62d46-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="62d46-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="62d46-119">Optional element.</span></span><br /><br /> <span data-ttu-id="62d46-120">定義資料的顯示方式，例如將資料向左或向右移位。</span><span class="sxs-lookup"><span data-stu-id="62d46-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="62d46-121">設定之控制項的 CustomItem 的 NewLine 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="62d46-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="62d46-122">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="62d46-122">Optional element.</span></span><br /><br /> <span data-ttu-id="62d46-123">將空白行加入控制項的顯示中。</span><span class="sxs-lookup"><span data-stu-id="62d46-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="62d46-124">設定之控制項的 CustomItem 的文字元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="62d46-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="62d46-125">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="62d46-125">Optional element.</span></span><br /><br /> <span data-ttu-id="62d46-126">將文字（例如括弧或括弧）新增至控制項的顯示。</span><span class="sxs-lookup"><span data-stu-id="62d46-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="62d46-127">父項目</span><span class="sxs-lookup"><span data-stu-id="62d46-127">Parent Elements</span></span>

|<span data-ttu-id="62d46-128">元素</span><span class="sxs-lookup"><span data-stu-id="62d46-128">Element</span></span>|<span data-ttu-id="62d46-129">描述</span><span class="sxs-lookup"><span data-stu-id="62d46-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="62d46-130">設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="62d46-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="62d46-131">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="62d46-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="62d46-132">備註</span><span class="sxs-lookup"><span data-stu-id="62d46-132">Remarks</span></span>

<span data-ttu-id="62d46-133">指定元素的子項目時 `CustomItem` ，請記住下列事項：</span><span class="sxs-lookup"><span data-stu-id="62d46-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="62d46-134">子項目必須以下列順序加入： `ExpressionBinding` 、 `NewLine` 、 `Text` 和 `Frame` 。</span><span class="sxs-lookup"><span data-stu-id="62d46-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="62d46-135">您可以指定的序列數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="62d46-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="62d46-136">在每個序列中， `ExpressionBinding` 您可以使用的元素數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="62d46-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="62d46-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62d46-137">See Also</span></span>

[<span data-ttu-id="62d46-138">設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="62d46-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="62d46-139">設定之控制項的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="62d46-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="62d46-140">設定之控制項的 CustomItem 的 NewLine 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="62d46-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="62d46-141">設定之控制項的 CustomItem 的文字元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="62d46-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="62d46-142">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="62d46-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
