---
title: View (Format) 的控制項之 CustomItem 的框架元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5ade36c183a026cb9001a2abbe91d31638a87108
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773448"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="e228a-102">檢視之控制項的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e228a-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="e228a-103">定義資料的顯示方式，例如將資料向左或向右移位。</span><span class="sxs-lookup"><span data-stu-id="e228a-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="e228a-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="e228a-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e228a-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 (格式) CustomEntries 專案的控制項的控制項 (的 CustomControl 元素針對 CustomControl for View (格式) 的 CustomEntries for 控制項的 CustomEntry 專案， (格式]) CustomItem 元素用於 view (format) Frame 元素 for view 的控制項 (格式) </span><span class="sxs-lookup"><span data-stu-id="e228a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e228a-106">語法</span><span class="sxs-lookup"><span data-stu-id="e228a-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e228a-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e228a-107">Attributes and Elements</span></span>

<span data-ttu-id="e228a-108">下列各節說明屬性、子專案和元素的父元素 `Frame` 。</span><span class="sxs-lookup"><span data-stu-id="e228a-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e228a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="e228a-109">Attributes</span></span>

<span data-ttu-id="e228a-110">無。</span><span class="sxs-lookup"><span data-stu-id="e228a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e228a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="e228a-111">Child Elements</span></span>

|<span data-ttu-id="e228a-112">元素</span><span class="sxs-lookup"><span data-stu-id="e228a-112">Element</span></span>|<span data-ttu-id="e228a-113">描述</span><span class="sxs-lookup"><span data-stu-id="e228a-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="e228a-114">必要元素</span><span class="sxs-lookup"><span data-stu-id="e228a-114">Required Element</span></span>|
|[<span data-ttu-id="e228a-115"> (格式之 View 控制項框架的 FirstLineHanging 元素) </span><span class="sxs-lookup"><span data-stu-id="e228a-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="e228a-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e228a-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e228a-117">指定第一行向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="e228a-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="e228a-118"> (格式之 View 控制項框架的 FirstLineIndent 元素) </span><span class="sxs-lookup"><span data-stu-id="e228a-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="e228a-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e228a-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e228a-120">指定第一行向右移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="e228a-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="e228a-121"> (格式之 View 控制項框架的 LeftIndent 元素) </span><span class="sxs-lookup"><span data-stu-id="e228a-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="e228a-122">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e228a-122">Optional element.</span></span><br /><br /> <span data-ttu-id="e228a-123">指定資料從左邊界下移的字元數。</span><span class="sxs-lookup"><span data-stu-id="e228a-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="e228a-124"> (格式之 View 控制項框架的 RightIndent 元素) </span><span class="sxs-lookup"><span data-stu-id="e228a-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="e228a-125">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e228a-125">Optional element.</span></span><br /><br /> <span data-ttu-id="e228a-126">指定資料從右邊界向外移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="e228a-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e228a-127">父項目</span><span class="sxs-lookup"><span data-stu-id="e228a-127">Parent Elements</span></span>

|<span data-ttu-id="e228a-128">元素</span><span class="sxs-lookup"><span data-stu-id="e228a-128">Element</span></span>|<span data-ttu-id="e228a-129">描述</span><span class="sxs-lookup"><span data-stu-id="e228a-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e228a-130">檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e228a-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="e228a-131">定義控制項所顯示的資料及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="e228a-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e228a-132">備註</span><span class="sxs-lookup"><span data-stu-id="e228a-132">Remarks</span></span>

<span data-ttu-id="e228a-133">您不能在相同的專案中指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)和[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md)元素 `Frame` 。</span><span class="sxs-lookup"><span data-stu-id="e228a-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="e228a-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e228a-134">See Also</span></span>

[<span data-ttu-id="e228a-135"> (格式之 View 控制項框架的 FirstLineHanging 元素) </span><span class="sxs-lookup"><span data-stu-id="e228a-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="e228a-136"> (格式之 View 控制項框架的 FirstLineIndent 元素) </span><span class="sxs-lookup"><span data-stu-id="e228a-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="e228a-137"> (格式之 View 控制項框架的 LeftIndent 元素) </span><span class="sxs-lookup"><span data-stu-id="e228a-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="e228a-138"> (格式之 View 控制項框架的 RightIndent 元素) </span><span class="sxs-lookup"><span data-stu-id="e228a-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="e228a-139">檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e228a-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="e228a-140">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="e228a-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
