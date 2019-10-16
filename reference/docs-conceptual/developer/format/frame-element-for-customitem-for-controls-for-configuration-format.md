---
title: 設定之控制項的 CustomItem 的框架元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363657"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="21746-102">設定之控制項的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="21746-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="21746-103">定義資料的顯示方式，例如將資料向左或向右移位。</span><span class="sxs-lookup"><span data-stu-id="21746-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="21746-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="21746-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="21746-105">Configuration 元素（格式）控制設定（format） CustomControl 元素的設定（格式）控制項專案的設定專案（格式） CustomControl 設定的 CustomEntries 元素（格式）Format） CustomEntry 元素，用於 CustomControl 控制項的 CustomItem 元素，用於 CustomEntry 的設定框架元素的控制項（格式）</span><span class="sxs-lookup"><span data-stu-id="21746-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="21746-106">語法</span><span class="sxs-lookup"><span data-stu-id="21746-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="21746-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="21746-107">Attributes and Elements</span></span>

<span data-ttu-id="21746-108">下列各節說明屬性、子專案，以及 `Frame` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="21746-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="21746-109">屬性</span><span class="sxs-lookup"><span data-stu-id="21746-109">Attributes</span></span>

<span data-ttu-id="21746-110">無。</span><span class="sxs-lookup"><span data-stu-id="21746-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="21746-111">子元素</span><span class="sxs-lookup"><span data-stu-id="21746-111">Child Elements</span></span>

|<span data-ttu-id="21746-112">元素</span><span class="sxs-lookup"><span data-stu-id="21746-112">Element</span></span>|<span data-ttu-id="21746-113">描述</span><span class="sxs-lookup"><span data-stu-id="21746-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="21746-114">必要元素</span><span class="sxs-lookup"><span data-stu-id="21746-114">Required Element</span></span>|
|[<span data-ttu-id="21746-115">設定之控制項的框架的 FirstLineHanging 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21746-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="21746-116">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="21746-116">Optional element.</span></span><br /><br /> <span data-ttu-id="21746-117">指定第一行資料向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="21746-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="21746-118">設定之控制項的框架的 FirstLineIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21746-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="21746-119">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="21746-119">Optional element.</span></span><br /><br /> <span data-ttu-id="21746-120">指定第一行資料向右移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="21746-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="21746-121">設定之控制項的框架的 LeftIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21746-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="21746-122">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="21746-122">Optional element.</span></span><br /><br /> <span data-ttu-id="21746-123">指定資料從左邊界下移的字元數。</span><span class="sxs-lookup"><span data-stu-id="21746-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="21746-124">設定之控制項的框架的 RightIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21746-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="21746-125">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="21746-125">Optional element.</span></span><br /><br /> <span data-ttu-id="21746-126">指定資料從右邊界向外移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="21746-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="21746-127">父元素</span><span class="sxs-lookup"><span data-stu-id="21746-127">Parent Elements</span></span>

|<span data-ttu-id="21746-128">元素</span><span class="sxs-lookup"><span data-stu-id="21746-128">Element</span></span>|<span data-ttu-id="21746-129">描述</span><span class="sxs-lookup"><span data-stu-id="21746-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="21746-130">設定之控制項的 CustomEntry 的 CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="21746-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="21746-131">定義控制項所顯示的資料及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="21746-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="21746-132">備註</span><span class="sxs-lookup"><span data-stu-id="21746-132">Remarks</span></span>

<span data-ttu-id="21746-133">您不能在相同的 `Frame` 元素中指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)和[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="21746-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="21746-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21746-134">See Also</span></span>

[<span data-ttu-id="21746-135">設定之控制項的框架的 FirstLineHanging 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21746-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="21746-136">設定之控制項的框架的 FirstLineIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21746-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="21746-137">設定之控制項的框架的 LeftIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21746-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="21746-138">設定之控制項的框架的 RightIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21746-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="21746-139">設定之控制項的 CustomEntry 的 CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="21746-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="21746-140">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="21746-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
