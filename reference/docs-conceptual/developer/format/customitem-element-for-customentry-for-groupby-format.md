---
title: GroupBy 之 CustomEntry 的 CustomItem 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363877"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="59a3c-102">GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="59a3c-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="59a3c-103">定義自訂控制項視圖顯示的資料，以及顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="59a3c-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="59a3c-104">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="59a3c-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="59a3c-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（format） CustomEntries 專案的 groupby （format） CustomControl 元素，適用于的 CustomControl for GroupBy （format） CustomItem 元素GroupBy 的 CustomEntry （格式）</span><span class="sxs-lookup"><span data-stu-id="59a3c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="59a3c-106">語法</span><span class="sxs-lookup"><span data-stu-id="59a3c-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="59a3c-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="59a3c-107">Attributes and Elements</span></span>

<span data-ttu-id="59a3c-108">下列各節說明屬性、子專案，以及 `CustomItem` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="59a3c-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="59a3c-109">屬性</span><span class="sxs-lookup"><span data-stu-id="59a3c-109">Attributes</span></span>

<span data-ttu-id="59a3c-110">無。</span><span class="sxs-lookup"><span data-stu-id="59a3c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="59a3c-111">子元素</span><span class="sxs-lookup"><span data-stu-id="59a3c-111">Child Elements</span></span>

|<span data-ttu-id="59a3c-112">元素</span><span class="sxs-lookup"><span data-stu-id="59a3c-112">Element</span></span>|<span data-ttu-id="59a3c-113">描述</span><span class="sxs-lookup"><span data-stu-id="59a3c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="59a3c-114">GroupBy 之 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="59a3c-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="59a3c-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="59a3c-115">Optional element.</span></span><br /><br /> <span data-ttu-id="59a3c-116">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="59a3c-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="59a3c-117">GroupBy 之 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="59a3c-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="59a3c-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="59a3c-118">Optional element.</span></span><br /><br /> <span data-ttu-id="59a3c-119">定義自訂控制項視圖顯示的資料，以及顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="59a3c-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="59a3c-120">GroupBy 的 CustomItem 的分行符號元素（格式）</span><span class="sxs-lookup"><span data-stu-id="59a3c-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="59a3c-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="59a3c-121">Optional element.</span></span><br /><br /> <span data-ttu-id="59a3c-122">將空白行加入控制項的顯示中。</span><span class="sxs-lookup"><span data-stu-id="59a3c-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="59a3c-123">GroupBy 的 CustomItem 的文字元素（格式）</span><span class="sxs-lookup"><span data-stu-id="59a3c-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="59a3c-124">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="59a3c-124">Optional element.</span></span><br /><br /> <span data-ttu-id="59a3c-125">指定控制項所顯示之資料的其他文字。</span><span class="sxs-lookup"><span data-stu-id="59a3c-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="59a3c-126">父元素</span><span class="sxs-lookup"><span data-stu-id="59a3c-126">Parent Elements</span></span>

|<span data-ttu-id="59a3c-127">元素</span><span class="sxs-lookup"><span data-stu-id="59a3c-127">Element</span></span>|<span data-ttu-id="59a3c-128">描述</span><span class="sxs-lookup"><span data-stu-id="59a3c-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="59a3c-129">GroupBy 之 CustomControl 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="59a3c-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="59a3c-130">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="59a3c-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="59a3c-131">備註</span><span class="sxs-lookup"><span data-stu-id="59a3c-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="59a3c-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59a3c-132">See Also</span></span>

[<span data-ttu-id="59a3c-133">GroupBy 之 CustomControl 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="59a3c-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="59a3c-134">GroupBy 之 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="59a3c-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="59a3c-135">GroupBy 之 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="59a3c-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="59a3c-136">GroupBy 的 CustomItem 的分行符號元素（格式）</span><span class="sxs-lookup"><span data-stu-id="59a3c-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="59a3c-137">GroupBy 的 CustomItem 的文字元素（格式）</span><span class="sxs-lookup"><span data-stu-id="59a3c-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="59a3c-138">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="59a3c-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
