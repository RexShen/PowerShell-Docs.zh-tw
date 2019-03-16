---
title: FirstLineHanging CustomControl 檢視 （格式） 的畫面格的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6ac3d86-0529-4b93-9bc7-ee94fcef9618
caps.latest.revision: 8
ms.openlocfilehash: ea43e025f5f653ff000e1d7591b535e73da5c9e5
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054215"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="e2978-102">檢視之 CustomControl 的框架的 FirstLineHanging 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e2978-102">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="e2978-103">指定資料的第一行向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="e2978-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="e2978-104">定義自訂控制項的檢視時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="e2978-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="e2978-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目 （格式） CustomEntries 項目 CustomControl CustomEntries 用於檢視 （格式） CustomItem 元素的檢視 （格式） CustomEntry 元素CustomEntry CustomControl CustomControl 檢視 （格式） 的畫面格的檢視 （格式） FirstLineHanging 項目的的 CustomItem CustomControlView （格式） 框架元素</span><span class="sxs-lookup"><span data-stu-id="e2978-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e2978-106">語法</span><span class="sxs-lookup"><span data-stu-id="e2978-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e2978-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="e2978-107">Attributes and Elements</span></span>

<span data-ttu-id="e2978-108">下列各節說明屬性、 子項目和父項目`FirstLineHanging`項目。</span><span class="sxs-lookup"><span data-stu-id="e2978-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e2978-109">屬性</span><span class="sxs-lookup"><span data-stu-id="e2978-109">Attributes</span></span>

<span data-ttu-id="e2978-110">無。</span><span class="sxs-lookup"><span data-stu-id="e2978-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e2978-111">子元素</span><span class="sxs-lookup"><span data-stu-id="e2978-111">Child Elements</span></span>

<span data-ttu-id="e2978-112">無。</span><span class="sxs-lookup"><span data-stu-id="e2978-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e2978-113">父元素</span><span class="sxs-lookup"><span data-stu-id="e2978-113">Parent Elements</span></span>

|<span data-ttu-id="e2978-114">元素</span><span class="sxs-lookup"><span data-stu-id="e2978-114">Element</span></span>|<span data-ttu-id="e2978-115">描述</span><span class="sxs-lookup"><span data-stu-id="e2978-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e2978-116">CustomControl 檢視 （格式） 的 CustomItem 的框架項目</span><span class="sxs-lookup"><span data-stu-id="e2978-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="e2978-117">定義資料的顯示方式，例如將資料轉移至左邊或右邊。</span><span class="sxs-lookup"><span data-stu-id="e2978-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e2978-118">文字值</span><span class="sxs-lookup"><span data-stu-id="e2978-118">Text Value</span></span>

<span data-ttu-id="e2978-119">指定您想要移動資料的第一行的字元數。</span><span class="sxs-lookup"><span data-stu-id="e2978-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="e2978-120">備註</span><span class="sxs-lookup"><span data-stu-id="e2978-120">Remarks</span></span>

<span data-ttu-id="e2978-121">如果未指定這個項目，您無法指定[FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)項目。</span><span class="sxs-lookup"><span data-stu-id="e2978-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2978-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2978-122">See Also</span></span>

[<span data-ttu-id="e2978-123">FirstLineIndent CustomControl 檢視 （格式） 的畫面格的項目</span><span class="sxs-lookup"><span data-stu-id="e2978-123">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e2978-124">CustomControl 檢視 （格式） 的 CustomItem 的框架項目</span><span class="sxs-lookup"><span data-stu-id="e2978-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e2978-125">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="e2978-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
