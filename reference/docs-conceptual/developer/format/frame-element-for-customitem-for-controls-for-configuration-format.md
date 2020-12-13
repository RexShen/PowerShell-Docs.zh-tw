---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 CustomItem 的框架元素 (格式)
description: 設定之控制項的 CustomItem 的框架元素 (格式)
ms.openlocfilehash: 85d095b9b0c25b68b2353bce56b85333aff91b98
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652239"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="8e6ce-103">設定之控制項的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8e6ce-103">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="8e6ce-104">定義顯示資料的方式，例如將資料向左或向右移動。</span><span class="sxs-lookup"><span data-stu-id="8e6ce-104">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="8e6ce-105">當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="8e6ce-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="8e6ce-106">設定專案 (格式) 控制項的設定專案 (格式設定的控制項) 控制項專案 (格式) CustomEntries 專案的 CustomControl 設定 (格式) 的設定 (格式) 的設定 (格式) CustomControl 的控制項設定 (格式) 格式的控制項的 CustomItem 專案</span><span class="sxs-lookup"><span data-stu-id="8e6ce-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8e6ce-107">語法</span><span class="sxs-lookup"><span data-stu-id="8e6ce-107">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8e6ce-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8e6ce-108">Attributes and Elements</span></span>

<span data-ttu-id="8e6ce-109">下列各節說明屬性、子專案和元素的父元素 `Frame` 。</span><span class="sxs-lookup"><span data-stu-id="8e6ce-109">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8e6ce-110">屬性</span><span class="sxs-lookup"><span data-stu-id="8e6ce-110">Attributes</span></span>

<span data-ttu-id="8e6ce-111">無。</span><span class="sxs-lookup"><span data-stu-id="8e6ce-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8e6ce-112">子元素</span><span class="sxs-lookup"><span data-stu-id="8e6ce-112">Child Elements</span></span>

|<span data-ttu-id="8e6ce-113">元素</span><span class="sxs-lookup"><span data-stu-id="8e6ce-113">Element</span></span>|<span data-ttu-id="8e6ce-114">描述</span><span class="sxs-lookup"><span data-stu-id="8e6ce-114">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="8e6ce-115">Required 元素</span><span class="sxs-lookup"><span data-stu-id="8e6ce-115">Required Element</span></span>|
|[<span data-ttu-id="8e6ce-116">設定之控制項的框架的 FirstLineHanging 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8e6ce-116">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="8e6ce-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="8e6ce-117">Optional element.</span></span><br /><br /> <span data-ttu-id="8e6ce-118">指定將第一行資料向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="8e6ce-118">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="8e6ce-119">設定之控制項的框架的 FirstLineIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8e6ce-119">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="8e6ce-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="8e6ce-120">Optional element.</span></span><br /><br /> <span data-ttu-id="8e6ce-121">指定第一行資料向右移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="8e6ce-121">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="8e6ce-122">設定之控制項的框架的 LeftIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8e6ce-122">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="8e6ce-123">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="8e6ce-123">Optional element.</span></span><br /><br /> <span data-ttu-id="8e6ce-124">指定資料從左邊界向外移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="8e6ce-124">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="8e6ce-125">設定之控制項的框架的 RightIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8e6ce-125">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="8e6ce-126">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="8e6ce-126">Optional element.</span></span><br /><br /> <span data-ttu-id="8e6ce-127">指定資料從右邊界向外移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="8e6ce-127">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8e6ce-128">父項目</span><span class="sxs-lookup"><span data-stu-id="8e6ce-128">Parent Elements</span></span>

|<span data-ttu-id="8e6ce-129">元素</span><span class="sxs-lookup"><span data-stu-id="8e6ce-129">Element</span></span>|<span data-ttu-id="8e6ce-130">描述</span><span class="sxs-lookup"><span data-stu-id="8e6ce-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8e6ce-131">適用于設定之控制項的 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="8e6ce-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="8e6ce-132">定義控制項顯示的資料以及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="8e6ce-132">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8e6ce-133">備註</span><span class="sxs-lookup"><span data-stu-id="8e6ce-133">Remarks</span></span>

<span data-ttu-id="8e6ce-134">您無法在相同的元素中指定 [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) 和 [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) 元素 `Frame` 。</span><span class="sxs-lookup"><span data-stu-id="8e6ce-134">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e6ce-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e6ce-135">See Also</span></span>

[<span data-ttu-id="8e6ce-136">設定之控制項的框架的 FirstLineHanging 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8e6ce-136">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="8e6ce-137">設定之控制項的框架的 FirstLineIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8e6ce-137">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="8e6ce-138">設定之控制項的框架的 LeftIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8e6ce-138">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="8e6ce-139">設定之控制項的框架的 RightIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8e6ce-139">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="8e6ce-140">適用于設定之控制項的 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="8e6ce-140">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="8e6ce-141">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="8e6ce-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
