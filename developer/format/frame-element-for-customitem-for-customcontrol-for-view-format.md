---
title: 畫面格元素 CustomItem CustomControl 的檢視 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054776"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="5f595-102">檢視之 CustomControl 的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5f595-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="5f595-103">定義資料的顯示方式，例如將資料轉移至左邊或右邊。</span><span class="sxs-lookup"><span data-stu-id="5f595-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="5f595-104">定義自訂控制項的檢視時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="5f595-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="5f595-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目 （格式） CustomEntries 項目 CustomControl CustomEntries 用於檢視 （格式） CustomItem 元素的檢視 （格式） CustomEntry 元素CustomEntry CustomControl 檢視 （格式） 的 CustomItem CustomControlView （格式） 框架元素</span><span class="sxs-lookup"><span data-stu-id="5f595-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5f595-106">語法</span><span class="sxs-lookup"><span data-stu-id="5f595-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5f595-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="5f595-107">Attributes and Elements</span></span>

<span data-ttu-id="5f595-108">下列各節說明屬性、 子項目和父項目`Frame`項目。</span><span class="sxs-lookup"><span data-stu-id="5f595-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5f595-109">屬性</span><span class="sxs-lookup"><span data-stu-id="5f595-109">Attributes</span></span>

<span data-ttu-id="5f595-110">無。</span><span class="sxs-lookup"><span data-stu-id="5f595-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5f595-111">子元素</span><span class="sxs-lookup"><span data-stu-id="5f595-111">Child Elements</span></span>

|<span data-ttu-id="5f595-112">元素</span><span class="sxs-lookup"><span data-stu-id="5f595-112">Element</span></span>|<span data-ttu-id="5f595-113">描述</span><span class="sxs-lookup"><span data-stu-id="5f595-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="5f595-114">必要項目</span><span class="sxs-lookup"><span data-stu-id="5f595-114">Required Element</span></span>|
|[<span data-ttu-id="5f595-115">FirstLineHanging 項目</span><span class="sxs-lookup"><span data-stu-id="5f595-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="5f595-116">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="5f595-116">Optional element.</span></span><br /><br /> <span data-ttu-id="5f595-117">指定資料的第一行向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="5f595-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="5f595-118">FirstLineIndent 項目</span><span class="sxs-lookup"><span data-stu-id="5f595-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="5f595-119">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="5f595-119">Optional element.</span></span><br /><br /> <span data-ttu-id="5f595-120">指定資料的第一行向右移位的字元數。</span><span class="sxs-lookup"><span data-stu-id="5f595-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="5f595-121">LeftIndent 項目</span><span class="sxs-lookup"><span data-stu-id="5f595-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="5f595-122">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="5f595-122">Optional element.</span></span><br /><br /> <span data-ttu-id="5f595-123">指定的資料會移離左邊界的字元數。</span><span class="sxs-lookup"><span data-stu-id="5f595-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="5f595-124">RightIndent 項目</span><span class="sxs-lookup"><span data-stu-id="5f595-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="5f595-125">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="5f595-125">Optional element.</span></span><br /><br /> <span data-ttu-id="5f595-126">指定的資料會移離右邊界的字元數。</span><span class="sxs-lookup"><span data-stu-id="5f595-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5f595-127">父元素</span><span class="sxs-lookup"><span data-stu-id="5f595-127">Parent Elements</span></span>

|<span data-ttu-id="5f595-128">元素</span><span class="sxs-lookup"><span data-stu-id="5f595-128">Element</span></span>|<span data-ttu-id="5f595-129">描述</span><span class="sxs-lookup"><span data-stu-id="5f595-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5f595-130">CustomItem CustomEntry 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="5f595-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="5f595-131">定義控制項所顯示的資料和顯示方式。</span><span class="sxs-lookup"><span data-stu-id="5f595-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5f595-132">備註</span><span class="sxs-lookup"><span data-stu-id="5f595-132">Remarks</span></span>

<span data-ttu-id="5f595-133">您無法指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)並[FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)在相同的項目`Frame`項目。</span><span class="sxs-lookup"><span data-stu-id="5f595-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f595-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f595-134">See Also</span></span>

[<span data-ttu-id="5f595-135">FirstLineHanging 項目</span><span class="sxs-lookup"><span data-stu-id="5f595-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5f595-136">FirstLineIndent 項目</span><span class="sxs-lookup"><span data-stu-id="5f595-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5f595-137">LeftIndent 項目</span><span class="sxs-lookup"><span data-stu-id="5f595-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5f595-138">RightIndent 項目</span><span class="sxs-lookup"><span data-stu-id="5f595-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5f595-139">CustomItem CustomEntry 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="5f595-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5f595-140">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="5f595-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
