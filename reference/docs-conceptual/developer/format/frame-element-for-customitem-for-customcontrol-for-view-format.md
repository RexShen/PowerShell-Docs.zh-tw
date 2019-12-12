---
title: CustomControl for View 的 CustomItem 的框架元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363637"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="2b6a4-102">檢視之 CustomControl 的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2b6a4-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="2b6a4-103">定義資料的顯示方式，例如將資料向左或向右移位。</span><span class="sxs-lookup"><span data-stu-id="2b6a4-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="2b6a4-104">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="2b6a4-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="2b6a4-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素（format） CustomEntries 元素，用於 CustomEntry for View （Format） CustomEntries 元素的 CustomControl for view （format） CustomItem 元素CustomItem for CustomControl for View 的 CustomEntry for CustomControlView （格式）框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2b6a4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2b6a4-106">語法</span><span class="sxs-lookup"><span data-stu-id="2b6a4-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2b6a4-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="2b6a4-107">Attributes and Elements</span></span>

<span data-ttu-id="2b6a4-108">下列各節說明屬性、子專案，以及 `Frame` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="2b6a4-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2b6a4-109">屬性</span><span class="sxs-lookup"><span data-stu-id="2b6a4-109">Attributes</span></span>

<span data-ttu-id="2b6a4-110">無。</span><span class="sxs-lookup"><span data-stu-id="2b6a4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2b6a4-111">子元素</span><span class="sxs-lookup"><span data-stu-id="2b6a4-111">Child Elements</span></span>

|<span data-ttu-id="2b6a4-112">元素</span><span class="sxs-lookup"><span data-stu-id="2b6a4-112">Element</span></span>|<span data-ttu-id="2b6a4-113">描述</span><span class="sxs-lookup"><span data-stu-id="2b6a4-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="2b6a4-114">必要元素</span><span class="sxs-lookup"><span data-stu-id="2b6a4-114">Required Element</span></span>|
|[<span data-ttu-id="2b6a4-115">FirstLineHanging 元素</span><span class="sxs-lookup"><span data-stu-id="2b6a4-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="2b6a4-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="2b6a4-116">Optional element.</span></span><br /><br /> <span data-ttu-id="2b6a4-117">指定第一行資料向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="2b6a4-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="2b6a4-118">FirstLineIndent 元素</span><span class="sxs-lookup"><span data-stu-id="2b6a4-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="2b6a4-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="2b6a4-119">Optional element.</span></span><br /><br /> <span data-ttu-id="2b6a4-120">指定第一行資料向右移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="2b6a4-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="2b6a4-121">LeftIndent 元素</span><span class="sxs-lookup"><span data-stu-id="2b6a4-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="2b6a4-122">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="2b6a4-122">Optional element.</span></span><br /><br /> <span data-ttu-id="2b6a4-123">指定資料從左邊界下移的字元數。</span><span class="sxs-lookup"><span data-stu-id="2b6a4-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="2b6a4-124">RightIndent 元素</span><span class="sxs-lookup"><span data-stu-id="2b6a4-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="2b6a4-125">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="2b6a4-125">Optional element.</span></span><br /><br /> <span data-ttu-id="2b6a4-126">指定資料從右邊界向外移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="2b6a4-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2b6a4-127">父元素</span><span class="sxs-lookup"><span data-stu-id="2b6a4-127">Parent Elements</span></span>

|<span data-ttu-id="2b6a4-128">元素</span><span class="sxs-lookup"><span data-stu-id="2b6a4-128">Element</span></span>|<span data-ttu-id="2b6a4-129">描述</span><span class="sxs-lookup"><span data-stu-id="2b6a4-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2b6a4-130">CustomEntry for View 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2b6a4-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="2b6a4-131">定義控制項所顯示的資料及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="2b6a4-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2b6a4-132">備註</span><span class="sxs-lookup"><span data-stu-id="2b6a4-132">Remarks</span></span>

<span data-ttu-id="2b6a4-133">您不能在相同的 `Frame` 元素中指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)和[FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="2b6a4-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="2b6a4-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b6a4-134">See Also</span></span>

[<span data-ttu-id="2b6a4-135">FirstLineHanging 元素</span><span class="sxs-lookup"><span data-stu-id="2b6a4-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2b6a4-136">FirstLineIndent 元素</span><span class="sxs-lookup"><span data-stu-id="2b6a4-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2b6a4-137">LeftIndent 元素</span><span class="sxs-lookup"><span data-stu-id="2b6a4-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2b6a4-138">RightIndent 元素</span><span class="sxs-lookup"><span data-stu-id="2b6a4-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2b6a4-139">CustomEntry for View 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2b6a4-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2b6a4-140">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="2b6a4-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
