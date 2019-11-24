---
title: View 之控制項的 CustomEntry 的 CustomItem 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363937"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="b7c64-102">檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b7c64-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="b7c64-103">定義控制項所顯示的資料及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="b7c64-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="b7c64-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="b7c64-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b7c64-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素CustomControl for View （Format） CustomEntry 元素 for CustomEntries for view （format） CustomItem 元素 for view （格式）的控制項 CustomEntry</span><span class="sxs-lookup"><span data-stu-id="b7c64-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b7c64-106">語法</span><span class="sxs-lookup"><span data-stu-id="b7c64-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b7c64-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="b7c64-107">Attributes and Elements</span></span>

<span data-ttu-id="b7c64-108">下列各節說明屬性、子專案，以及 `CustomItem` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="b7c64-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="b7c64-109">如需詳細資訊，請參閱備註。</span><span class="sxs-lookup"><span data-stu-id="b7c64-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="b7c64-110">屬性</span><span class="sxs-lookup"><span data-stu-id="b7c64-110">Attributes</span></span>

<span data-ttu-id="b7c64-111">無。</span><span class="sxs-lookup"><span data-stu-id="b7c64-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b7c64-112">子元素</span><span class="sxs-lookup"><span data-stu-id="b7c64-112">Child Elements</span></span>

|<span data-ttu-id="b7c64-113">項目</span><span class="sxs-lookup"><span data-stu-id="b7c64-113">Element</span></span>|<span data-ttu-id="b7c64-114">說明</span><span class="sxs-lookup"><span data-stu-id="b7c64-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7c64-115">View 之控制項的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7c64-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="b7c64-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="b7c64-116">Optional element.</span></span><br /><br /> <span data-ttu-id="b7c64-117">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="b7c64-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="b7c64-118">View 之控制項的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7c64-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="b7c64-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="b7c64-119">Optional element.</span></span><br /><br /> <span data-ttu-id="b7c64-120">定義資料的顯示方式，例如將資料向左或向右移位。</span><span class="sxs-lookup"><span data-stu-id="b7c64-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="b7c64-121">View 之控制項的 CustomItem 的分行符號元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7c64-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="b7c64-122">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="b7c64-122">Optional element.</span></span><br /><br /> <span data-ttu-id="b7c64-123">將空白行加入控制項的顯示中。</span><span class="sxs-lookup"><span data-stu-id="b7c64-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="b7c64-124">View 之控制項的 CustomItem 的文字元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7c64-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="b7c64-125">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="b7c64-125">Optional element.</span></span><br /><br /> <span data-ttu-id="b7c64-126">將文字（例如括弧或括弧）新增至控制項的顯示。</span><span class="sxs-lookup"><span data-stu-id="b7c64-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b7c64-127">父元素</span><span class="sxs-lookup"><span data-stu-id="b7c64-127">Parent Elements</span></span>

|<span data-ttu-id="b7c64-128">項目</span><span class="sxs-lookup"><span data-stu-id="b7c64-128">Element</span></span>|<span data-ttu-id="b7c64-129">說明</span><span class="sxs-lookup"><span data-stu-id="b7c64-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7c64-130">View 之控制項的 CustomEntries 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7c64-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="b7c64-131">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="b7c64-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b7c64-132">備註</span><span class="sxs-lookup"><span data-stu-id="b7c64-132">Remarks</span></span>

<span data-ttu-id="b7c64-133">指定 `CustomItem` 元素的子項目時，請記住下列事項：</span><span class="sxs-lookup"><span data-stu-id="b7c64-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="b7c64-134">子項目必須以下列順序加入： `ExpressionBinding`、`NewLine`、`Text`和 `Frame`。</span><span class="sxs-lookup"><span data-stu-id="b7c64-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="b7c64-135">您可以指定的序列數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="b7c64-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="b7c64-136">在每個序列中，您可以使用的 `ExpressionBinding` 元素數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="b7c64-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7c64-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7c64-137">See Also</span></span>

[<span data-ttu-id="b7c64-138">View 之控制項的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7c64-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="b7c64-139">View 之控制項的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7c64-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="b7c64-140">View 之控制項的 CustomItem 的分行符號元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7c64-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="b7c64-141">View 之控制項的 CustomItem 的文字元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b7c64-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="b7c64-142">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="b7c64-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
