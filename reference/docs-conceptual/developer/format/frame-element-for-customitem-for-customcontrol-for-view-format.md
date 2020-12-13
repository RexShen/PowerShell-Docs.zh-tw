---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之 CustomControl 的 CustomItem 的框架元素 (格式)
description: 檢視之 CustomControl 的 CustomItem 的框架元素 (格式)
ms.openlocfilehash: 1ffe071bb6c4f590e4c79803a3faff2108c7b636
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652187"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="f6c8c-103">檢視之 CustomControl 的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="f6c8c-103">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="f6c8c-104">定義顯示資料的方式，例如將資料向左或向右移動。</span><span class="sxs-lookup"><span data-stu-id="f6c8c-104">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="f6c8c-105">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="f6c8c-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="f6c8c-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) CustomControl 元素 (格式) CustomEntries 專案 (格式) 專案 (格式) CustomEntry 專案 (格式) CustomEntries 專案 CustomItem for CustomEntry 的 CustomControlView 專案 (格式) CustomItem for CustomControl 的專案格式</span><span class="sxs-lookup"><span data-stu-id="f6c8c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f6c8c-107">語法</span><span class="sxs-lookup"><span data-stu-id="f6c8c-107">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f6c8c-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f6c8c-108">Attributes and Elements</span></span>

<span data-ttu-id="f6c8c-109">下列各節說明屬性、子專案和元素的父元素 `Frame` 。</span><span class="sxs-lookup"><span data-stu-id="f6c8c-109">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f6c8c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f6c8c-110">Attributes</span></span>

<span data-ttu-id="f6c8c-111">無。</span><span class="sxs-lookup"><span data-stu-id="f6c8c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f6c8c-112">子元素</span><span class="sxs-lookup"><span data-stu-id="f6c8c-112">Child Elements</span></span>

|<span data-ttu-id="f6c8c-113">元素</span><span class="sxs-lookup"><span data-stu-id="f6c8c-113">Element</span></span>|<span data-ttu-id="f6c8c-114">描述</span><span class="sxs-lookup"><span data-stu-id="f6c8c-114">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="f6c8c-115">Required 元素</span><span class="sxs-lookup"><span data-stu-id="f6c8c-115">Required Element</span></span>|
|[<span data-ttu-id="f6c8c-116">FirstLineHanging 元素</span><span class="sxs-lookup"><span data-stu-id="f6c8c-116">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="f6c8c-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f6c8c-117">Optional element.</span></span><br /><br /> <span data-ttu-id="f6c8c-118">指定將第一行資料向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="f6c8c-118">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="f6c8c-119">FirstLineIndent 元素</span><span class="sxs-lookup"><span data-stu-id="f6c8c-119">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="f6c8c-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f6c8c-120">Optional element.</span></span><br /><br /> <span data-ttu-id="f6c8c-121">指定第一行資料向右移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="f6c8c-121">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="f6c8c-122">LeftIndent 元素</span><span class="sxs-lookup"><span data-stu-id="f6c8c-122">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="f6c8c-123">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f6c8c-123">Optional element.</span></span><br /><br /> <span data-ttu-id="f6c8c-124">指定資料從左邊界向外移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="f6c8c-124">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="f6c8c-125">RightIndent 元素</span><span class="sxs-lookup"><span data-stu-id="f6c8c-125">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="f6c8c-126">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f6c8c-126">Optional element.</span></span><br /><br /> <span data-ttu-id="f6c8c-127">指定資料從右邊界向外移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="f6c8c-127">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f6c8c-128">父項目</span><span class="sxs-lookup"><span data-stu-id="f6c8c-128">Parent Elements</span></span>

|<span data-ttu-id="f6c8c-129">元素</span><span class="sxs-lookup"><span data-stu-id="f6c8c-129">Element</span></span>|<span data-ttu-id="f6c8c-130">描述</span><span class="sxs-lookup"><span data-stu-id="f6c8c-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f6c8c-131">適用于 CustomEntry 的 CustomItem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="f6c8c-131">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="f6c8c-132">定義控制項顯示的資料以及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="f6c8c-132">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f6c8c-133">備註</span><span class="sxs-lookup"><span data-stu-id="f6c8c-133">Remarks</span></span>

<span data-ttu-id="f6c8c-134">您無法在相同的元素中指定 [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) 和 [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) 元素 `Frame` 。</span><span class="sxs-lookup"><span data-stu-id="f6c8c-134">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="f6c8c-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6c8c-135">See Also</span></span>

[<span data-ttu-id="f6c8c-136">FirstLineHanging 元素</span><span class="sxs-lookup"><span data-stu-id="f6c8c-136">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f6c8c-137">FirstLineIndent 元素</span><span class="sxs-lookup"><span data-stu-id="f6c8c-137">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f6c8c-138">LeftIndent 元素</span><span class="sxs-lookup"><span data-stu-id="f6c8c-138">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f6c8c-139">RightIndent 元素</span><span class="sxs-lookup"><span data-stu-id="f6c8c-139">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f6c8c-140">適用于 CustomEntry 的 CustomItem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="f6c8c-140">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f6c8c-141">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="f6c8c-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
