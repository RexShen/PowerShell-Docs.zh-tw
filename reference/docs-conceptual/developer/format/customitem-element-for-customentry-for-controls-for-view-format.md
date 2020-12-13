---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)
description: 檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)
ms.openlocfilehash: 67bff97c27cfedf046b17eea438efcd66ae2ee4a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666751"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="7c643-103">檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7c643-103">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="7c643-104">定義控制項顯示的資料以及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="7c643-104">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="7c643-105">當定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="7c643-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="7c643-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) Control 元素 (format) Control 元素 (format) format (CustomEntries) format 控制項控制項的控制項 (格式) 專案 (格式)  (格式控制項的控制項) 格式 CustomEntry 專案格式的控制項 CustomEntries 元素格式的控制項</span><span class="sxs-lookup"><span data-stu-id="7c643-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7c643-107">語法</span><span class="sxs-lookup"><span data-stu-id="7c643-107">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7c643-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7c643-108">Attributes and Elements</span></span>

<span data-ttu-id="7c643-109">下列各節說明屬性、子專案和元素的父元素 `CustomItem` 。</span><span class="sxs-lookup"><span data-stu-id="7c643-109">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="7c643-110">如需詳細資訊，請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="7c643-110">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="7c643-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7c643-111">Attributes</span></span>

<span data-ttu-id="7c643-112">無。</span><span class="sxs-lookup"><span data-stu-id="7c643-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7c643-113">子元素</span><span class="sxs-lookup"><span data-stu-id="7c643-113">Child Elements</span></span>

|<span data-ttu-id="7c643-114">元素</span><span class="sxs-lookup"><span data-stu-id="7c643-114">Element</span></span>|<span data-ttu-id="7c643-115">描述</span><span class="sxs-lookup"><span data-stu-id="7c643-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7c643-116">檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7c643-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="7c643-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="7c643-117">Optional element.</span></span><br /><br /> <span data-ttu-id="7c643-118">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="7c643-118">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="7c643-119">檢視之控制項的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7c643-119">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="7c643-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="7c643-120">Optional element.</span></span><br /><br /> <span data-ttu-id="7c643-121">定義顯示資料的方式，例如將資料向左或向右移動。</span><span class="sxs-lookup"><span data-stu-id="7c643-121">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="7c643-122">檢視之控制項的 CustomItem 的 NewLine 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7c643-122">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="7c643-123">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="7c643-123">Optional element.</span></span><br /><br /> <span data-ttu-id="7c643-124">在控制項的顯示中加入空白行。</span><span class="sxs-lookup"><span data-stu-id="7c643-124">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="7c643-125">檢視之控制項的 CustomItem 的文字元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7c643-125">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="7c643-126">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="7c643-126">Optional element.</span></span><br /><br /> <span data-ttu-id="7c643-127">將文字（例如括弧或括弧）新增至控制項的顯示。</span><span class="sxs-lookup"><span data-stu-id="7c643-127">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7c643-128">父項目</span><span class="sxs-lookup"><span data-stu-id="7c643-128">Parent Elements</span></span>

|<span data-ttu-id="7c643-129">元素</span><span class="sxs-lookup"><span data-stu-id="7c643-129">Element</span></span>|<span data-ttu-id="7c643-130">描述</span><span class="sxs-lookup"><span data-stu-id="7c643-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7c643-131">檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7c643-131">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="7c643-132">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="7c643-132">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7c643-133">備註</span><span class="sxs-lookup"><span data-stu-id="7c643-133">Remarks</span></span>

<span data-ttu-id="7c643-134">指定元素的子項目時 `CustomItem` ，請記住下列事項：</span><span class="sxs-lookup"><span data-stu-id="7c643-134">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="7c643-135">子項目必須以下列順序加入： `ExpressionBinding` 、 `NewLine` 、 `Text` 和 `Frame` 。</span><span class="sxs-lookup"><span data-stu-id="7c643-135">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="7c643-136">您可以指定的序列數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="7c643-136">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="7c643-137">在每個序列中，您可以使用的元素數目沒有最大限制 `ExpressionBinding` 。</span><span class="sxs-lookup"><span data-stu-id="7c643-137">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c643-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c643-138">See Also</span></span>

[<span data-ttu-id="7c643-139">檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7c643-139">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="7c643-140">檢視之控制項的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7c643-140">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="7c643-141">檢視之控制項的 CustomItem 的 NewLine 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7c643-141">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="7c643-142">檢視之控制項的 CustomItem 的文字元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7c643-142">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="7c643-143">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="7c643-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
