---
title: View (Format) 的控制項之 CustomEntry 的 CustomItem 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 747ea14e7118be62ebee00e7d80af2dccb5c8353
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785841"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="1f672-102">檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1f672-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="1f672-103">定義控制項所顯示的資料及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="1f672-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="1f672-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="1f672-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="1f672-105">Configuration 專案 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 CustomControl 格式 (CustomEntries 專案用於 view) format (CustomEntry 元素 for view) 格式的控制項 (CustomEntries 專案（適用于視圖) 格式之控制項的 CustomItem (</span><span class="sxs-lookup"><span data-stu-id="1f672-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1f672-106">語法</span><span class="sxs-lookup"><span data-stu-id="1f672-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1f672-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1f672-107">Attributes and Elements</span></span>

<span data-ttu-id="1f672-108">下列各節說明屬性、子專案和元素的父元素 `CustomItem` 。</span><span class="sxs-lookup"><span data-stu-id="1f672-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="1f672-109">如需詳細資訊，請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="1f672-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f672-110">屬性</span><span class="sxs-lookup"><span data-stu-id="1f672-110">Attributes</span></span>

<span data-ttu-id="1f672-111">無。</span><span class="sxs-lookup"><span data-stu-id="1f672-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1f672-112">子元素</span><span class="sxs-lookup"><span data-stu-id="1f672-112">Child Elements</span></span>

|<span data-ttu-id="1f672-113">元素</span><span class="sxs-lookup"><span data-stu-id="1f672-113">Element</span></span>|<span data-ttu-id="1f672-114">描述</span><span class="sxs-lookup"><span data-stu-id="1f672-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f672-115">檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1f672-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="1f672-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="1f672-116">Optional element.</span></span><br /><br /> <span data-ttu-id="1f672-117">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="1f672-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="1f672-118">檢視之控制項的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1f672-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="1f672-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="1f672-119">Optional element.</span></span><br /><br /> <span data-ttu-id="1f672-120">定義資料的顯示方式，例如將資料向左或向右移位。</span><span class="sxs-lookup"><span data-stu-id="1f672-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="1f672-121">檢視之控制項的 CustomItem 的 NewLine 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1f672-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="1f672-122">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="1f672-122">Optional element.</span></span><br /><br /> <span data-ttu-id="1f672-123">將空白行加入控制項的顯示中。</span><span class="sxs-lookup"><span data-stu-id="1f672-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="1f672-124">檢視之控制項的 CustomItem 的文字元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1f672-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="1f672-125">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="1f672-125">Optional element.</span></span><br /><br /> <span data-ttu-id="1f672-126">將文字（例如括弧或括弧）新增至控制項的顯示。</span><span class="sxs-lookup"><span data-stu-id="1f672-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1f672-127">父項目</span><span class="sxs-lookup"><span data-stu-id="1f672-127">Parent Elements</span></span>

|<span data-ttu-id="1f672-128">元素</span><span class="sxs-lookup"><span data-stu-id="1f672-128">Element</span></span>|<span data-ttu-id="1f672-129">描述</span><span class="sxs-lookup"><span data-stu-id="1f672-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f672-130">檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1f672-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="1f672-131">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="1f672-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1f672-132">備註</span><span class="sxs-lookup"><span data-stu-id="1f672-132">Remarks</span></span>

<span data-ttu-id="1f672-133">指定元素的子項目時 `CustomItem` ，請記住下列事項：</span><span class="sxs-lookup"><span data-stu-id="1f672-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="1f672-134">子項目必須以下列順序加入： `ExpressionBinding` 、 `NewLine` 、 `Text` 和 `Frame` 。</span><span class="sxs-lookup"><span data-stu-id="1f672-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="1f672-135">您可以指定的序列數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="1f672-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="1f672-136">在每個序列中， `ExpressionBinding` 您可以使用的元素數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="1f672-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f672-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f672-137">See Also</span></span>

[<span data-ttu-id="1f672-138">檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1f672-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="1f672-139">檢視之控制項的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1f672-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="1f672-140">檢視之控制項的 CustomItem 的 NewLine 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1f672-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="1f672-141">檢視之控制項的 CustomItem 的文字元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1f672-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="1f672-142">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="1f672-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
