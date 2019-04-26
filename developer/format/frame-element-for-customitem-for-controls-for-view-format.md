---
title: 針對 CustomItem 框架項目控制項的檢視 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065711"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="bd5d0-102">檢視之控制項的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bd5d0-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="bd5d0-103">定義資料的顯示方式，例如將資料轉移至左邊或右邊。</span><span class="sxs-lookup"><span data-stu-id="bd5d0-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="bd5d0-104">定義可供檢視的控制項時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="bd5d0-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="bd5d0-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目CustomControl CustomEntries CustomEntry 如 CustomItem 用於檢視 （格式） 的控制項的檢視 （格式） 框架項目控制項的檢視 （格式） CustomItem 元素的控制項的檢視 （格式） CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="bd5d0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bd5d0-106">語法</span><span class="sxs-lookup"><span data-stu-id="bd5d0-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bd5d0-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bd5d0-107">Attributes and Elements</span></span>

<span data-ttu-id="bd5d0-108">下列各節說明屬性、 子項目和父項目`Frame`項目。</span><span class="sxs-lookup"><span data-stu-id="bd5d0-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bd5d0-109">屬性</span><span class="sxs-lookup"><span data-stu-id="bd5d0-109">Attributes</span></span>

<span data-ttu-id="bd5d0-110">無。</span><span class="sxs-lookup"><span data-stu-id="bd5d0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bd5d0-111">子元素</span><span class="sxs-lookup"><span data-stu-id="bd5d0-111">Child Elements</span></span>

|<span data-ttu-id="bd5d0-112">元素</span><span class="sxs-lookup"><span data-stu-id="bd5d0-112">Element</span></span>|<span data-ttu-id="bd5d0-113">描述</span><span class="sxs-lookup"><span data-stu-id="bd5d0-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="bd5d0-114">必要項目</span><span class="sxs-lookup"><span data-stu-id="bd5d0-114">Required Element</span></span>|
|[<span data-ttu-id="bd5d0-115">控制項的檢視 （格式） 的框架 FirstLineHanging 項目</span><span class="sxs-lookup"><span data-stu-id="bd5d0-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="bd5d0-116">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="bd5d0-116">Optional element.</span></span><br /><br /> <span data-ttu-id="bd5d0-117">指定的第一行向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="bd5d0-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="bd5d0-118">控制項的檢視 （格式） 的框架 FirstLineIndent 項目</span><span class="sxs-lookup"><span data-stu-id="bd5d0-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="bd5d0-119">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="bd5d0-119">Optional element.</span></span><br /><br /> <span data-ttu-id="bd5d0-120">指定的第一行向右移位的字元數。</span><span class="sxs-lookup"><span data-stu-id="bd5d0-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="bd5d0-121">控制項的檢視 （格式） 的框架 LeftIndent 項目</span><span class="sxs-lookup"><span data-stu-id="bd5d0-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="bd5d0-122">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="bd5d0-122">Optional element.</span></span><br /><br /> <span data-ttu-id="bd5d0-123">指定的資料會移離左邊界的字元數。</span><span class="sxs-lookup"><span data-stu-id="bd5d0-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="bd5d0-124">控制項的檢視 （格式） 的框架 RightIndent 項目</span><span class="sxs-lookup"><span data-stu-id="bd5d0-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="bd5d0-125">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="bd5d0-125">Optional element.</span></span><br /><br /> <span data-ttu-id="bd5d0-126">指定的資料會移離右邊界的字元數。</span><span class="sxs-lookup"><span data-stu-id="bd5d0-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bd5d0-127">父項目</span><span class="sxs-lookup"><span data-stu-id="bd5d0-127">Parent Elements</span></span>

|<span data-ttu-id="bd5d0-128">項目</span><span class="sxs-lookup"><span data-stu-id="bd5d0-128">Element</span></span>|<span data-ttu-id="bd5d0-129">描述</span><span class="sxs-lookup"><span data-stu-id="bd5d0-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bd5d0-130">用於檢視 （格式） 的控制項 CustomEntry CustomItem 項目</span><span class="sxs-lookup"><span data-stu-id="bd5d0-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="bd5d0-131">定義控制項所顯示的資料和顯示方式。</span><span class="sxs-lookup"><span data-stu-id="bd5d0-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bd5d0-132">備註</span><span class="sxs-lookup"><span data-stu-id="bd5d0-132">Remarks</span></span>

<span data-ttu-id="bd5d0-133">您無法指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)並[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md)在相同的項目`Frame`項目。</span><span class="sxs-lookup"><span data-stu-id="bd5d0-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="bd5d0-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd5d0-134">See Also</span></span>

[<span data-ttu-id="bd5d0-135">控制項的檢視 （格式） 的框架 FirstLineHanging 項目</span><span class="sxs-lookup"><span data-stu-id="bd5d0-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="bd5d0-136">控制項的檢視 （格式） 的框架 FirstLineIndent 項目</span><span class="sxs-lookup"><span data-stu-id="bd5d0-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="bd5d0-137">控制項的檢視 （格式） 的框架 LeftIndent 項目</span><span class="sxs-lookup"><span data-stu-id="bd5d0-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="bd5d0-138">控制項的檢視 （格式） 的框架 RightIndent 項目</span><span class="sxs-lookup"><span data-stu-id="bd5d0-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="bd5d0-139">用於檢視 （格式） 的控制項 CustomEntry CustomItem 項目</span><span class="sxs-lookup"><span data-stu-id="bd5d0-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="bd5d0-140">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="bd5d0-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
