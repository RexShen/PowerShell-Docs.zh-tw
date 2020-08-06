---
title: CustomControl for View (格式) 的 CustomEntry 的 CustomItem 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 25101c9c156ef91657f51db7044bf9a6653142a2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785824"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="4e172-102">檢視之 CustomControl 的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4e172-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="4e172-103">定義自訂控制項視圖顯示的資料，以及顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="4e172-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="4e172-104">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="4e172-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="4e172-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 專案 (格式) CustomControl for view (CustomEntry 元素（CustomEntries for view) CustomItem 元素的 CustomEntry for view (格式) </span><span class="sxs-lookup"><span data-stu-id="4e172-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4e172-106">語法</span><span class="sxs-lookup"><span data-stu-id="4e172-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4e172-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4e172-107">Attributes and Elements</span></span>

<span data-ttu-id="4e172-108">下列各節說明屬性、子專案和元素的父元素 `CustomItem` 。</span><span class="sxs-lookup"><span data-stu-id="4e172-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4e172-109">屬性</span><span class="sxs-lookup"><span data-stu-id="4e172-109">Attributes</span></span>

<span data-ttu-id="4e172-110">無。</span><span class="sxs-lookup"><span data-stu-id="4e172-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4e172-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4e172-111">Child Elements</span></span>

|<span data-ttu-id="4e172-112">元素</span><span class="sxs-lookup"><span data-stu-id="4e172-112">Element</span></span>|<span data-ttu-id="4e172-113">描述</span><span class="sxs-lookup"><span data-stu-id="4e172-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4e172-114">檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4e172-114">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="4e172-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="4e172-115">Optional element.</span></span><br /><br /> <span data-ttu-id="4e172-116">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="4e172-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="4e172-117">檢視之 CustomControl 的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4e172-117">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="4e172-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="4e172-118">Optional element.</span></span><br /><br /> <span data-ttu-id="4e172-119">定義自訂控制項視圖顯示的資料，以及顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="4e172-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="4e172-120"> (格式之自訂控制項的 CustomItem 的分行符號元素) </span><span class="sxs-lookup"><span data-stu-id="4e172-120">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="4e172-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="4e172-121">Optional element.</span></span><br /><br /> <span data-ttu-id="4e172-122">將空白行加入控制項的顯示中。</span><span class="sxs-lookup"><span data-stu-id="4e172-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="4e172-123">CustomItem for CustomControl for View (Format 的 Text 元素) </span><span class="sxs-lookup"><span data-stu-id="4e172-123">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="4e172-124">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="4e172-124">Optional element.</span></span><br /><br /> <span data-ttu-id="4e172-125">指定控制項所顯示之資料的其他文字。</span><span class="sxs-lookup"><span data-stu-id="4e172-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4e172-126">父項目</span><span class="sxs-lookup"><span data-stu-id="4e172-126">Parent Elements</span></span>

|<span data-ttu-id="4e172-127">元素</span><span class="sxs-lookup"><span data-stu-id="4e172-127">Element</span></span>|<span data-ttu-id="4e172-128">描述</span><span class="sxs-lookup"><span data-stu-id="4e172-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4e172-129">檢視之 CustomControl 的 CustomEntries 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4e172-129">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="4e172-130">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="4e172-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4e172-131">備註</span><span class="sxs-lookup"><span data-stu-id="4e172-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="4e172-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e172-132">See Also</span></span>

[<span data-ttu-id="4e172-133">CustomEntries for View (格式的 CustomEntry 元素) </span><span class="sxs-lookup"><span data-stu-id="4e172-133">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4e172-134">檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4e172-134">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4e172-135">檢視之 CustomControl 的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4e172-135">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4e172-136">檢視之 CustomControl 的 CustomItem 的 NewLine 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4e172-136">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4e172-137">CustomItem for CustomControl for View (Format 的 Text 元素) </span><span class="sxs-lookup"><span data-stu-id="4e172-137">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="4e172-138">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="4e172-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
