---
title: " (格式) 設定之控制項的 CustomItem 的框架元素 |Microsoft Docs"
ms.date: 09/13/2016
ms.openlocfilehash: fa435b8d6b868d2d7c94b7926321d94edc2ec290
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781472"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="4b5ab-102">設定之控制項的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4b5ab-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="4b5ab-103">定義資料的顯示方式，例如將資料向左或向右移位。</span><span class="sxs-lookup"><span data-stu-id="4b5ab-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="4b5ab-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="4b5ab-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="4b5ab-105">Configuration 專案 (格式) 控制設定的控制項元素 (格式設定 (格式的控制項) 控制元素) 設定 (格式的 CustomControl 的 CustomEntries 元素) 設定 (格式) CustomControl 元素適用于設定 (格式之控制項的 CustomItem 的設定) CustomEntry (格式的控制專案的 CustomEntry 的控制項</span><span class="sxs-lookup"><span data-stu-id="4b5ab-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4b5ab-106">語法</span><span class="sxs-lookup"><span data-stu-id="4b5ab-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4b5ab-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4b5ab-107">Attributes and Elements</span></span>

<span data-ttu-id="4b5ab-108">下列各節說明屬性、子專案和元素的父元素 `Frame` 。</span><span class="sxs-lookup"><span data-stu-id="4b5ab-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4b5ab-109">屬性</span><span class="sxs-lookup"><span data-stu-id="4b5ab-109">Attributes</span></span>

<span data-ttu-id="4b5ab-110">無。</span><span class="sxs-lookup"><span data-stu-id="4b5ab-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4b5ab-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4b5ab-111">Child Elements</span></span>

|<span data-ttu-id="4b5ab-112">元素</span><span class="sxs-lookup"><span data-stu-id="4b5ab-112">Element</span></span>|<span data-ttu-id="4b5ab-113">描述</span><span class="sxs-lookup"><span data-stu-id="4b5ab-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="4b5ab-114">必要元素</span><span class="sxs-lookup"><span data-stu-id="4b5ab-114">Required Element</span></span>|
|[<span data-ttu-id="4b5ab-115">設定之控制項的框架的 FirstLineHanging 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4b5ab-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="4b5ab-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="4b5ab-116">Optional element.</span></span><br /><br /> <span data-ttu-id="4b5ab-117">指定第一行資料向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="4b5ab-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="4b5ab-118">設定之控制項的框架的 FirstLineIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4b5ab-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="4b5ab-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="4b5ab-119">Optional element.</span></span><br /><br /> <span data-ttu-id="4b5ab-120">指定第一行資料向右移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="4b5ab-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="4b5ab-121">設定之控制項的框架的 LeftIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4b5ab-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="4b5ab-122">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="4b5ab-122">Optional element.</span></span><br /><br /> <span data-ttu-id="4b5ab-123">指定資料從左邊界下移的字元數。</span><span class="sxs-lookup"><span data-stu-id="4b5ab-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="4b5ab-124">設定之控制項的框架的 RightIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4b5ab-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="4b5ab-125">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="4b5ab-125">Optional element.</span></span><br /><br /> <span data-ttu-id="4b5ab-126">指定資料從右邊界向外移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="4b5ab-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4b5ab-127">父項目</span><span class="sxs-lookup"><span data-stu-id="4b5ab-127">Parent Elements</span></span>

|<span data-ttu-id="4b5ab-128">元素</span><span class="sxs-lookup"><span data-stu-id="4b5ab-128">Element</span></span>|<span data-ttu-id="4b5ab-129">描述</span><span class="sxs-lookup"><span data-stu-id="4b5ab-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4b5ab-130">設定之控制項的 CustomEntry 的 CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="4b5ab-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="4b5ab-131">定義控制項所顯示的資料及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="4b5ab-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4b5ab-132">備註</span><span class="sxs-lookup"><span data-stu-id="4b5ab-132">Remarks</span></span>

<span data-ttu-id="4b5ab-133">您不能在相同的專案中指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)和[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)元素 `Frame` 。</span><span class="sxs-lookup"><span data-stu-id="4b5ab-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b5ab-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b5ab-134">See Also</span></span>

[<span data-ttu-id="4b5ab-135">設定之控制項的框架的 FirstLineHanging 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4b5ab-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="4b5ab-136">設定之控制項的框架的 FirstLineIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4b5ab-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="4b5ab-137">設定之控制項的框架的 LeftIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4b5ab-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="4b5ab-138">設定之控制項的框架的 RightIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4b5ab-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="4b5ab-139">設定之控制項的 CustomEntry 的 CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="4b5ab-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="4b5ab-140">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="4b5ab-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
