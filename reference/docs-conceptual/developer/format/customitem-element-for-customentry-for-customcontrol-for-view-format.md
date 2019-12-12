---
title: CustomControl for View 的 CustomEntry 的 CustomItem 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363947"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="18390-102">檢視之 CustomControl 的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="18390-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="18390-103">定義自訂控制項視圖顯示的資料，以及顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="18390-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="18390-104">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="18390-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="18390-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素（format） CustomEntries 元素，用於 CustomEntry for View （Format） CustomEntries 元素的 CustomControl for view （format） CustomItem 元素CustomEntry for View （格式）</span><span class="sxs-lookup"><span data-stu-id="18390-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="18390-106">語法</span><span class="sxs-lookup"><span data-stu-id="18390-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="18390-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="18390-107">Attributes and Elements</span></span>

<span data-ttu-id="18390-108">下列各節說明屬性、子專案，以及 `CustomItem` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="18390-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="18390-109">屬性</span><span class="sxs-lookup"><span data-stu-id="18390-109">Attributes</span></span>

<span data-ttu-id="18390-110">無。</span><span class="sxs-lookup"><span data-stu-id="18390-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="18390-111">子元素</span><span class="sxs-lookup"><span data-stu-id="18390-111">Child Elements</span></span>

|<span data-ttu-id="18390-112">元素</span><span class="sxs-lookup"><span data-stu-id="18390-112">Element</span></span>|<span data-ttu-id="18390-113">描述</span><span class="sxs-lookup"><span data-stu-id="18390-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="18390-114">CustomControl for View 的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="18390-114">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="18390-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="18390-115">Optional element.</span></span><br /><br /> <span data-ttu-id="18390-116">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="18390-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="18390-117">適用于 CustomControl for View 的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="18390-117">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="18390-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="18390-118">Optional element.</span></span><br /><br /> <span data-ttu-id="18390-119">定義自訂控制項視圖顯示的資料，以及顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="18390-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="18390-120">View 的自訂控制項的 CustomItem 的分行符號元素（格式）</span><span class="sxs-lookup"><span data-stu-id="18390-120">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="18390-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="18390-121">Optional element.</span></span><br /><br /> <span data-ttu-id="18390-122">將空白行加入控制項的顯示中。</span><span class="sxs-lookup"><span data-stu-id="18390-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="18390-123">CustomItem for CustomControl for View 的 Text 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="18390-123">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="18390-124">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="18390-124">Optional element.</span></span><br /><br /> <span data-ttu-id="18390-125">指定控制項所顯示之資料的其他文字。</span><span class="sxs-lookup"><span data-stu-id="18390-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="18390-126">父元素</span><span class="sxs-lookup"><span data-stu-id="18390-126">Parent Elements</span></span>

|<span data-ttu-id="18390-127">元素</span><span class="sxs-lookup"><span data-stu-id="18390-127">Element</span></span>|<span data-ttu-id="18390-128">描述</span><span class="sxs-lookup"><span data-stu-id="18390-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="18390-129">CustomControl for View 的 CustomEntries 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="18390-129">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="18390-130">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="18390-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="18390-131">備註</span><span class="sxs-lookup"><span data-stu-id="18390-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="18390-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18390-132">See Also</span></span>

[<span data-ttu-id="18390-133">CustomEntries for View 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="18390-133">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="18390-134">CustomControl for View 的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="18390-134">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="18390-135">適用于 CustomControl for View 的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="18390-135">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="18390-136">CustomControl for View 的 CustomItem 的換行元素（格式）</span><span class="sxs-lookup"><span data-stu-id="18390-136">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="18390-137">CustomItem for CustomControl for View 的 Text 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="18390-137">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="18390-138">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="18390-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
