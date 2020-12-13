---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之 CustomItem 的框架元素 (格式)
description: GroupBy 之 CustomItem 的框架元素 (格式)
ms.openlocfilehash: 86b51766974ebfcae06583ade237a77c6db92866
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652167"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="fba78-103">GroupBy 之 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fba78-103">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="fba78-104">定義顯示資料的方式，例如將資料向左或向右移動。</span><span class="sxs-lookup"><span data-stu-id="fba78-104">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="fba78-105">定義如何顯示新的物件群組時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="fba78-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="fba78-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 專案的視圖 (格式) CustomEntries 元素適用于 GroupBy (格式) 元素用於 CustomEntry 的 groupby (格式)  (格式的 CustomControl 專案) 格式 (的 CustomItem 專案) 格式 (</span><span class="sxs-lookup"><span data-stu-id="fba78-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fba78-107">語法</span><span class="sxs-lookup"><span data-stu-id="fba78-107">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fba78-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fba78-108">Attributes and Elements</span></span>

<span data-ttu-id="fba78-109">下列各節說明屬性、子專案和元素的父元素 `Frame` 。</span><span class="sxs-lookup"><span data-stu-id="fba78-109">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fba78-110">屬性</span><span class="sxs-lookup"><span data-stu-id="fba78-110">Attributes</span></span>

<span data-ttu-id="fba78-111">無。</span><span class="sxs-lookup"><span data-stu-id="fba78-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fba78-112">子元素</span><span class="sxs-lookup"><span data-stu-id="fba78-112">Child Elements</span></span>

|<span data-ttu-id="fba78-113">元素</span><span class="sxs-lookup"><span data-stu-id="fba78-113">Element</span></span>|<span data-ttu-id="fba78-114">描述</span><span class="sxs-lookup"><span data-stu-id="fba78-114">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="fba78-115">Required 元素</span><span class="sxs-lookup"><span data-stu-id="fba78-115">Required Element</span></span>|
|[<span data-ttu-id="fba78-116">GroupBy 之框架的 FirstLineHanging 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fba78-116">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="fba78-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="fba78-117">Optional element.</span></span><br /><br /> <span data-ttu-id="fba78-118">指定將第一行資料向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="fba78-118">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="fba78-119">GroupBy 之框架的 FirstLineIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fba78-119">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="fba78-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="fba78-120">Optional element.</span></span><br /><br /> <span data-ttu-id="fba78-121">指定第一行資料向右移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="fba78-121">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="fba78-122">GroupBy 之框架的 LeftIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fba78-122">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="fba78-123">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="fba78-123">Optional element.</span></span><br /><br /> <span data-ttu-id="fba78-124">指定資料從左邊界向外移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="fba78-124">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="fba78-125">[GroupBy (格式之框架的 RightIndent 元素) ](./rightindent-element-for-frame-for-groupby-format.md)RightIndent 元素</span><span class="sxs-lookup"><span data-stu-id="fba78-125">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="fba78-126">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="fba78-126">Optional element.</span></span><br /><br /> <span data-ttu-id="fba78-127">指定資料從右邊界向外移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="fba78-127">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fba78-128">父項目</span><span class="sxs-lookup"><span data-stu-id="fba78-128">Parent Elements</span></span>

|<span data-ttu-id="fba78-129">元素</span><span class="sxs-lookup"><span data-stu-id="fba78-129">Element</span></span>|<span data-ttu-id="fba78-130">描述</span><span class="sxs-lookup"><span data-stu-id="fba78-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fba78-131">GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fba78-131">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="fba78-132">定義控制項顯示的資料以及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="fba78-132">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fba78-133">備註</span><span class="sxs-lookup"><span data-stu-id="fba78-133">Remarks</span></span>

<span data-ttu-id="fba78-134">您無法在相同的元素中指定 [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) 和 [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) 元素 `Frame` 。</span><span class="sxs-lookup"><span data-stu-id="fba78-134">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="fba78-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fba78-135">See Also</span></span>

[<span data-ttu-id="fba78-136">GroupBy 之框架的 FirstLineHanging 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fba78-136">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="fba78-137">GroupBy 之框架的 FirstLineIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fba78-137">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="fba78-138">GroupBy 之框架的 LeftIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fba78-138">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="fba78-139">GroupBy 之框架的 RightIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fba78-139">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="fba78-140">GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fba78-140">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="fba78-141">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="fba78-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
