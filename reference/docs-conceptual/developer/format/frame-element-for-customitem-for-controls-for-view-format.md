---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的 CustomItem 的框架元素 (格式)
description: 檢視之控制項的 CustomItem 的框架元素 (格式)
ms.openlocfilehash: 6f26e19a6894ac213b924108a56cb80f9ffd1143
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652207"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="d11af-103">檢視之控制項的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d11af-103">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="d11af-104">定義顯示資料的方式，例如將資料向左或向右移動。</span><span class="sxs-lookup"><span data-stu-id="d11af-104">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="d11af-105">當定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="d11af-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="d11af-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式) 控制項專案 (格式) CustomEntries 專案的視圖控制項的控制項 (格式若為 CustomControl for View (格式) CustomEntry 元素，用於 CustomEntries 的控制項 (格式) CustomEntry for 控制項的 CustomItem 專案 (格式)  () 格式控制項的控制項的框架元素</span><span class="sxs-lookup"><span data-stu-id="d11af-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d11af-107">語法</span><span class="sxs-lookup"><span data-stu-id="d11af-107">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d11af-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d11af-108">Attributes and Elements</span></span>

<span data-ttu-id="d11af-109">下列各節說明屬性、子專案和元素的父元素 `Frame` 。</span><span class="sxs-lookup"><span data-stu-id="d11af-109">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d11af-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d11af-110">Attributes</span></span>

<span data-ttu-id="d11af-111">無。</span><span class="sxs-lookup"><span data-stu-id="d11af-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d11af-112">子元素</span><span class="sxs-lookup"><span data-stu-id="d11af-112">Child Elements</span></span>

|<span data-ttu-id="d11af-113">元素</span><span class="sxs-lookup"><span data-stu-id="d11af-113">Element</span></span>|<span data-ttu-id="d11af-114">描述</span><span class="sxs-lookup"><span data-stu-id="d11af-114">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="d11af-115">Required 元素</span><span class="sxs-lookup"><span data-stu-id="d11af-115">Required Element</span></span>|
|[<span data-ttu-id="d11af-116">View (格式之控制項框架的 FirstLineHanging 元素) </span><span class="sxs-lookup"><span data-stu-id="d11af-116">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="d11af-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="d11af-117">Optional element.</span></span><br /><br /> <span data-ttu-id="d11af-118">指定第一行向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="d11af-118">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="d11af-119">View (格式之控制項框架的 FirstLineIndent 元素) </span><span class="sxs-lookup"><span data-stu-id="d11af-119">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="d11af-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="d11af-120">Optional element.</span></span><br /><br /> <span data-ttu-id="d11af-121">指定第一行向右移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="d11af-121">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="d11af-122">View (格式之控制項框架的 LeftIndent 元素) </span><span class="sxs-lookup"><span data-stu-id="d11af-122">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="d11af-123">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="d11af-123">Optional element.</span></span><br /><br /> <span data-ttu-id="d11af-124">指定資料從左邊界向外移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="d11af-124">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="d11af-125">View (格式之控制項框架的 RightIndent 元素) </span><span class="sxs-lookup"><span data-stu-id="d11af-125">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="d11af-126">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="d11af-126">Optional element.</span></span><br /><br /> <span data-ttu-id="d11af-127">指定資料從右邊界向外移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="d11af-127">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d11af-128">父項目</span><span class="sxs-lookup"><span data-stu-id="d11af-128">Parent Elements</span></span>

|<span data-ttu-id="d11af-129">元素</span><span class="sxs-lookup"><span data-stu-id="d11af-129">Element</span></span>|<span data-ttu-id="d11af-130">描述</span><span class="sxs-lookup"><span data-stu-id="d11af-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d11af-131">檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d11af-131">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="d11af-132">定義控制項顯示的資料以及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="d11af-132">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d11af-133">備註</span><span class="sxs-lookup"><span data-stu-id="d11af-133">Remarks</span></span>

<span data-ttu-id="d11af-134">您無法在相同的元素中指定 [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) 和 [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) 元素 `Frame` 。</span><span class="sxs-lookup"><span data-stu-id="d11af-134">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="d11af-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d11af-135">See Also</span></span>

[<span data-ttu-id="d11af-136">View (格式之控制項框架的 FirstLineHanging 元素) </span><span class="sxs-lookup"><span data-stu-id="d11af-136">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="d11af-137">View (格式之控制項框架的 FirstLineIndent 元素) </span><span class="sxs-lookup"><span data-stu-id="d11af-137">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="d11af-138">View (格式之控制項框架的 LeftIndent 元素) </span><span class="sxs-lookup"><span data-stu-id="d11af-138">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="d11af-139">View (格式之控制項框架的 RightIndent 元素) </span><span class="sxs-lookup"><span data-stu-id="d11af-139">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="d11af-140">檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d11af-140">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="d11af-141">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="d11af-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
