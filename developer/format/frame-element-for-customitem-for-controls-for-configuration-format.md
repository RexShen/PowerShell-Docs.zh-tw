---
title: 針對 CustomItem 框架項目控制項的組態 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862974"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="e5389-102">設定之控制項的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e5389-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e5389-103">定義資料的顯示方式，例如將資料轉移至左邊或右邊。</span><span class="sxs-lookup"><span data-stu-id="e5389-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="e5389-104">定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="e5389-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e5389-105">組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目CustomControl CustomEntry 組態框架項目 CustomItem 組態 （格式） 的控制項的控制項的組態 （格式） CustomItem 元素的控制項的格式） CustomEntry 項目</span><span class="sxs-lookup"><span data-stu-id="e5389-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5389-106">語法</span><span class="sxs-lookup"><span data-stu-id="e5389-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5389-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="e5389-107">Attributes and Elements</span></span>

<span data-ttu-id="e5389-108">下列各節說明屬性、 子項目和父項目`Frame`項目。</span><span class="sxs-lookup"><span data-stu-id="e5389-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5389-109">屬性</span><span class="sxs-lookup"><span data-stu-id="e5389-109">Attributes</span></span>

<span data-ttu-id="e5389-110">無。</span><span class="sxs-lookup"><span data-stu-id="e5389-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5389-111">子元素</span><span class="sxs-lookup"><span data-stu-id="e5389-111">Child Elements</span></span>

|<span data-ttu-id="e5389-112">元素</span><span class="sxs-lookup"><span data-stu-id="e5389-112">Element</span></span>|<span data-ttu-id="e5389-113">描述</span><span class="sxs-lookup"><span data-stu-id="e5389-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="e5389-114">必要項目</span><span class="sxs-lookup"><span data-stu-id="e5389-114">Required Element</span></span>|
|[<span data-ttu-id="e5389-115">FirstLineHanging 組態 （格式） 的控制項的畫面格的項目</span><span class="sxs-lookup"><span data-stu-id="e5389-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="e5389-116">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="e5389-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e5389-117">指定資料的第一行向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="e5389-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="e5389-118">FirstLineIndent 組態 （格式） 的控制項的畫面格的項目</span><span class="sxs-lookup"><span data-stu-id="e5389-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="e5389-119">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="e5389-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e5389-120">指定資料的第一行向右移位的字元數。</span><span class="sxs-lookup"><span data-stu-id="e5389-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="e5389-121">LeftIndent 組態 （格式） 的控制項的畫面格的項目</span><span class="sxs-lookup"><span data-stu-id="e5389-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="e5389-122">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="e5389-122">Optional element.</span></span><br /><br /> <span data-ttu-id="e5389-123">指定的資料會移離左邊界的字元數。</span><span class="sxs-lookup"><span data-stu-id="e5389-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="e5389-124">RightIndent 組態 （格式） 的控制項的畫面格的項目</span><span class="sxs-lookup"><span data-stu-id="e5389-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="e5389-125">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="e5389-125">Optional element.</span></span><br /><br /> <span data-ttu-id="e5389-126">指定的資料會移離右邊界的字元數。</span><span class="sxs-lookup"><span data-stu-id="e5389-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e5389-127">父元素</span><span class="sxs-lookup"><span data-stu-id="e5389-127">Parent Elements</span></span>

|<span data-ttu-id="e5389-128">元素</span><span class="sxs-lookup"><span data-stu-id="e5389-128">Element</span></span>|<span data-ttu-id="e5389-129">描述</span><span class="sxs-lookup"><span data-stu-id="e5389-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5389-130">組態控制項 CustomEntry CustomItem 項目</span><span class="sxs-lookup"><span data-stu-id="e5389-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="e5389-131">定義控制項所顯示的資料和顯示方式。</span><span class="sxs-lookup"><span data-stu-id="e5389-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e5389-132">備註</span><span class="sxs-lookup"><span data-stu-id="e5389-132">Remarks</span></span>

<span data-ttu-id="e5389-133">您無法指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)並[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)在相同的項目`Frame`項目。</span><span class="sxs-lookup"><span data-stu-id="e5389-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5389-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5389-134">See Also</span></span>

[<span data-ttu-id="e5389-135">FirstLineHanging 組態 （格式） 的控制項的畫面格的項目</span><span class="sxs-lookup"><span data-stu-id="e5389-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="e5389-136">FirstLineIndent 組態 （格式） 的控制項的畫面格的項目</span><span class="sxs-lookup"><span data-stu-id="e5389-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="e5389-137">LeftIndent 組態 （格式） 的控制項的畫面格的項目</span><span class="sxs-lookup"><span data-stu-id="e5389-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="e5389-138">RightIndent 組態 （格式） 的控制項的畫面格的項目</span><span class="sxs-lookup"><span data-stu-id="e5389-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="e5389-139">組態控制項 CustomEntry CustomItem 項目</span><span class="sxs-lookup"><span data-stu-id="e5389-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="e5389-140">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="e5389-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
