---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之框架的 FirstLineHanging 元素 (格式)
description: GroupBy 之框架的 FirstLineHanging 元素 (格式)
ms.openlocfilehash: 6a4ded9cced484440636aee694cd8381b2889ba8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652272"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a><span data-ttu-id="e5f36-103">GroupBy 之框架的 FirstLineHanging 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e5f36-103">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>

<span data-ttu-id="e5f36-104">指定將第一行資料向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="e5f36-104">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="e5f36-105">定義如何顯示新的物件群組時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="e5f36-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e5f36-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 專案 (格式) GroupBy 專案的視圖 (格式) 適用于 groupby (格式) CustomEntries 專案 (格式) 專案的專案 (格式)  (格式)  (格式的) CustomEntry 專案 (格式) 的格式</span><span class="sxs-lookup"><span data-stu-id="e5f36-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format) FirstLineHanging Element for Frame for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5f36-107">語法</span><span class="sxs-lookup"><span data-stu-id="e5f36-107">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5f36-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e5f36-108">Attributes and Elements</span></span>

<span data-ttu-id="e5f36-109">下列各節描述專案的屬性、子項目和父元素 `FirstLineHanging` 。</span><span class="sxs-lookup"><span data-stu-id="e5f36-109">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5f36-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e5f36-110">Attributes</span></span>

<span data-ttu-id="e5f36-111">無。</span><span class="sxs-lookup"><span data-stu-id="e5f36-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5f36-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e5f36-112">Child Elements</span></span>

<span data-ttu-id="e5f36-113">無。</span><span class="sxs-lookup"><span data-stu-id="e5f36-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e5f36-114">父項目</span><span class="sxs-lookup"><span data-stu-id="e5f36-114">Parent Elements</span></span>

|<span data-ttu-id="e5f36-115">元素</span><span class="sxs-lookup"><span data-stu-id="e5f36-115">Element</span></span>|<span data-ttu-id="e5f36-116">描述</span><span class="sxs-lookup"><span data-stu-id="e5f36-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5f36-117">GroupBy 之 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e5f36-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="e5f36-118">定義顯示資料的方式，例如將資料向左或向右移動。</span><span class="sxs-lookup"><span data-stu-id="e5f36-118">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e5f36-119">文字值</span><span class="sxs-lookup"><span data-stu-id="e5f36-119">Text Value</span></span>

<span data-ttu-id="e5f36-120">指定您想要將資料行移到第一行的字元數。</span><span class="sxs-lookup"><span data-stu-id="e5f36-120">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5f36-121">備註</span><span class="sxs-lookup"><span data-stu-id="e5f36-121">Remarks</span></span>

<span data-ttu-id="e5f36-122">如果指定了此元素，您就無法指定 [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="e5f36-122">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5f36-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5f36-123">See Also</span></span>

[<span data-ttu-id="e5f36-124">GroupBy 之框架的 FirstLineIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e5f36-124">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="e5f36-125">GroupBy 之 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e5f36-125">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="e5f36-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="e5f36-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
