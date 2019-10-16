---
title: View 之控制項的 CustomItem 的框架元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363647"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="f882d-102">檢視之控制項的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="f882d-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="f882d-103">定義資料的顯示方式，例如將資料向左或向右移位。</span><span class="sxs-lookup"><span data-stu-id="f882d-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="f882d-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="f882d-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="f882d-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素CustomControl for View （format） CustomEntry 元素 for CustomEntries for view （format） CustomItem 元素 for view （format） Frame 元素 for view （格式）之控制項的 CustomEntry</span><span class="sxs-lookup"><span data-stu-id="f882d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f882d-106">語法</span><span class="sxs-lookup"><span data-stu-id="f882d-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f882d-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="f882d-107">Attributes and Elements</span></span>

<span data-ttu-id="f882d-108">下列各節說明屬性、子專案，以及 `Frame` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="f882d-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f882d-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f882d-109">Attributes</span></span>

<span data-ttu-id="f882d-110">無。</span><span class="sxs-lookup"><span data-stu-id="f882d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f882d-111">子元素</span><span class="sxs-lookup"><span data-stu-id="f882d-111">Child Elements</span></span>

|<span data-ttu-id="f882d-112">元素</span><span class="sxs-lookup"><span data-stu-id="f882d-112">Element</span></span>|<span data-ttu-id="f882d-113">描述</span><span class="sxs-lookup"><span data-stu-id="f882d-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="f882d-114">必要元素</span><span class="sxs-lookup"><span data-stu-id="f882d-114">Required Element</span></span>|
|[<span data-ttu-id="f882d-115">View 控制項框架的 FirstLineHanging 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f882d-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="f882d-116">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="f882d-116">Optional element.</span></span><br /><br /> <span data-ttu-id="f882d-117">指定第一行向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="f882d-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="f882d-118">View 控制項框架的 FirstLineIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f882d-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="f882d-119">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="f882d-119">Optional element.</span></span><br /><br /> <span data-ttu-id="f882d-120">指定第一行向右移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="f882d-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="f882d-121">View 控制項框架的 LeftIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f882d-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="f882d-122">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="f882d-122">Optional element.</span></span><br /><br /> <span data-ttu-id="f882d-123">指定資料從左邊界下移的字元數。</span><span class="sxs-lookup"><span data-stu-id="f882d-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="f882d-124">View 控制項框架的 RightIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f882d-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="f882d-125">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="f882d-125">Optional element.</span></span><br /><br /> <span data-ttu-id="f882d-126">指定資料從右邊界向外移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="f882d-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f882d-127">父元素</span><span class="sxs-lookup"><span data-stu-id="f882d-127">Parent Elements</span></span>

|<span data-ttu-id="f882d-128">元素</span><span class="sxs-lookup"><span data-stu-id="f882d-128">Element</span></span>|<span data-ttu-id="f882d-129">描述</span><span class="sxs-lookup"><span data-stu-id="f882d-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f882d-130">View 之控制項的 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f882d-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="f882d-131">定義控制項所顯示的資料及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="f882d-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f882d-132">備註</span><span class="sxs-lookup"><span data-stu-id="f882d-132">Remarks</span></span>

<span data-ttu-id="f882d-133">您不能在相同的 `Frame` 元素中指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)和[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="f882d-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="f882d-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f882d-134">See Also</span></span>

[<span data-ttu-id="f882d-135">View 控制項框架的 FirstLineHanging 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f882d-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="f882d-136">View 控制項框架的 FirstLineIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f882d-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="f882d-137">View 控制項框架的 LeftIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f882d-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="f882d-138">View 控制項框架的 RightIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f882d-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="f882d-139">View 之控制項的 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f882d-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="f882d-140">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="f882d-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
