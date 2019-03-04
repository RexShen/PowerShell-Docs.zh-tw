---
title: 框架 CustomItem GroupBy （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854844"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="cc23a-102">GroupBy 之 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="cc23a-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="cc23a-103">定義資料的顯示方式，例如將資料轉移至左邊或右邊。</span><span class="sxs-lookup"><span data-stu-id="cc23a-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="cc23a-104">定義新的群組物件的顯示方式時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="cc23a-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="cc23a-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素CustomControl CustomEntry CustomItem 的 GroupBy （格式） 的 GroupBy （格式） 框架元素的 GroupBy （格式） CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="cc23a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cc23a-106">語法</span><span class="sxs-lookup"><span data-stu-id="cc23a-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cc23a-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="cc23a-107">Attributes and Elements</span></span>

<span data-ttu-id="cc23a-108">下列各節說明屬性、 子項目和父項目`Frame`項目。</span><span class="sxs-lookup"><span data-stu-id="cc23a-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cc23a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="cc23a-109">Attributes</span></span>

<span data-ttu-id="cc23a-110">無。</span><span class="sxs-lookup"><span data-stu-id="cc23a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cc23a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="cc23a-111">Child Elements</span></span>

|<span data-ttu-id="cc23a-112">元素</span><span class="sxs-lookup"><span data-stu-id="cc23a-112">Element</span></span>|<span data-ttu-id="cc23a-113">描述</span><span class="sxs-lookup"><span data-stu-id="cc23a-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="cc23a-114">必要項目</span><span class="sxs-lookup"><span data-stu-id="cc23a-114">Required Element</span></span>|
|[<span data-ttu-id="cc23a-115">GroupBy （格式） 的畫面格 FirstLineHanging 項目</span><span class="sxs-lookup"><span data-stu-id="cc23a-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="cc23a-116">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="cc23a-116">Optional element.</span></span><br /><br /> <span data-ttu-id="cc23a-117">指定資料的第一行向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="cc23a-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="cc23a-118">GroupBy （格式） 的畫面格 FirstLineIndent 項目</span><span class="sxs-lookup"><span data-stu-id="cc23a-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="cc23a-119">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="cc23a-119">Optional element.</span></span><br /><br /> <span data-ttu-id="cc23a-120">指定資料的第一行向右移位的字元數。</span><span class="sxs-lookup"><span data-stu-id="cc23a-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="cc23a-121">GroupBy （格式） 的畫面格 LeftIndent 項目</span><span class="sxs-lookup"><span data-stu-id="cc23a-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="cc23a-122">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="cc23a-122">Optional element.</span></span><br /><br /> <span data-ttu-id="cc23a-123">指定的資料會移離左邊界的字元數。</span><span class="sxs-lookup"><span data-stu-id="cc23a-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="cc23a-124">[GroupBy （格式） 的畫面格 RightIndent 元素](./rightindent-element-for-frame-for-groupby-format.md)RightIndent 項目</span><span class="sxs-lookup"><span data-stu-id="cc23a-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="cc23a-125">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="cc23a-125">Optional element.</span></span><br /><br /> <span data-ttu-id="cc23a-126">指定的資料會移離右邊界的字元數。</span><span class="sxs-lookup"><span data-stu-id="cc23a-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cc23a-127">父元素</span><span class="sxs-lookup"><span data-stu-id="cc23a-127">Parent Elements</span></span>

|<span data-ttu-id="cc23a-128">元素</span><span class="sxs-lookup"><span data-stu-id="cc23a-128">Element</span></span>|<span data-ttu-id="cc23a-129">描述</span><span class="sxs-lookup"><span data-stu-id="cc23a-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cc23a-130">GroupBy （格式） 的 CustomEntry CustomItem 項目</span><span class="sxs-lookup"><span data-stu-id="cc23a-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="cc23a-131">定義控制項所顯示的資料和顯示方式。</span><span class="sxs-lookup"><span data-stu-id="cc23a-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cc23a-132">備註</span><span class="sxs-lookup"><span data-stu-id="cc23a-132">Remarks</span></span>

<span data-ttu-id="cc23a-133">您無法指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md)並[FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md)在相同的項目`Frame`項目。</span><span class="sxs-lookup"><span data-stu-id="cc23a-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc23a-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc23a-134">See Also</span></span>

[<span data-ttu-id="cc23a-135">GroupBy （格式） 的畫面格 FirstLineHanging 項目</span><span class="sxs-lookup"><span data-stu-id="cc23a-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="cc23a-136">GroupBy （格式） 的畫面格 FirstLineIndent 項目</span><span class="sxs-lookup"><span data-stu-id="cc23a-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="cc23a-137">GroupBy （格式） 的畫面格 LeftIndent 項目</span><span class="sxs-lookup"><span data-stu-id="cc23a-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="cc23a-138">GroupBy （格式） 的畫面格 RightIndent 項目</span><span class="sxs-lookup"><span data-stu-id="cc23a-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="cc23a-139">GroupBy （格式） 的 CustomEntry CustomItem 項目</span><span class="sxs-lookup"><span data-stu-id="cc23a-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="cc23a-140">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="cc23a-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
