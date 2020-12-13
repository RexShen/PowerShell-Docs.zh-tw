---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的框架的 FirstLineHanging 元素 (格式)
description: 設定之控制項的框架的 FirstLineHanging 元素 (格式)
ms.openlocfilehash: 94d59ef7b54e036f76e38a3b06b769700443b9fb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655238"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="e1ae6-103">設定之控制項的框架的 FirstLineHanging 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e1ae6-103">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e1ae6-104">指定將第一行資料向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="e1ae6-104">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="e1ae6-105">當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="e1ae6-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e1ae6-106">設定元素 (格式) 控制項的設定元素 (格式) 控制項的設定 (格式) CustomControl 元素，用於 CustomControl 的設定 (格式) CustomEntry 元素針對設定 (格式的控制項的 CustomControl 格式) CustomItem 元素，用於 CustomEntry 的設定框架專案控制項的設定 (格式 (設定的控制項框架) FirstLineHanging 元素) </span><span class="sxs-lookup"><span data-stu-id="e1ae6-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e1ae6-107">語法</span><span class="sxs-lookup"><span data-stu-id="e1ae6-107">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e1ae6-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e1ae6-108">Attributes and Elements</span></span>

<span data-ttu-id="e1ae6-109">下列各節描述專案的屬性、子項目和父元素 `FirstLineHanging` 。</span><span class="sxs-lookup"><span data-stu-id="e1ae6-109">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e1ae6-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e1ae6-110">Attributes</span></span>

<span data-ttu-id="e1ae6-111">無。</span><span class="sxs-lookup"><span data-stu-id="e1ae6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e1ae6-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e1ae6-112">Child Elements</span></span>

<span data-ttu-id="e1ae6-113">無。</span><span class="sxs-lookup"><span data-stu-id="e1ae6-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e1ae6-114">父項目</span><span class="sxs-lookup"><span data-stu-id="e1ae6-114">Parent Elements</span></span>

|<span data-ttu-id="e1ae6-115">元素</span><span class="sxs-lookup"><span data-stu-id="e1ae6-115">Element</span></span>|<span data-ttu-id="e1ae6-116">描述</span><span class="sxs-lookup"><span data-stu-id="e1ae6-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1ae6-117">設定之控制項的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e1ae6-117">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="e1ae6-118">定義顯示資料的方式，例如將資料向左或向右移動。</span><span class="sxs-lookup"><span data-stu-id="e1ae6-118">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e1ae6-119">文字值</span><span class="sxs-lookup"><span data-stu-id="e1ae6-119">Text Value</span></span>

<span data-ttu-id="e1ae6-120">指定您想要將資料行移到第一行的字元數。</span><span class="sxs-lookup"><span data-stu-id="e1ae6-120">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="e1ae6-121">備註</span><span class="sxs-lookup"><span data-stu-id="e1ae6-121">Remarks</span></span>

<span data-ttu-id="e1ae6-122">如果指定這個元素，您就無法指定 `FirstLineIndent` 元素。</span><span class="sxs-lookup"><span data-stu-id="e1ae6-122">If this element is specified, you cannot specify the `FirstLineIndent` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1ae6-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1ae6-123">See Also</span></span>

[<span data-ttu-id="e1ae6-124">設定之控制項的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e1ae6-124">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="e1ae6-125">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="e1ae6-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
