---
title: FirstLineIndent CustomControl 檢視 （格式） 的畫面格的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 9ec6caedcb7cf20d4aab2216cd8a9707269d9452
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854954"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="0a3fd-102">檢視之 CustomControl 的框架的 FirstLineIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0a3fd-102">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="0a3fd-103">指定資料的第一行向右移位的字元數。</span><span class="sxs-lookup"><span data-stu-id="0a3fd-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="0a3fd-104">定義自訂控制項的檢視時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="0a3fd-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="0a3fd-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目 （格式） CustomEntries 項目 CustomControl CustomEntries 用於檢視 （格式） CustomItem 元素的檢視 （格式） CustomEntry 元素CustomEntry CutomControlView （格式） 的檢視 （格式） FirstLineIndent 項目的 CustomControl CustomItem 框架元素</span><span class="sxs-lookup"><span data-stu-id="0a3fd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CutomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineIndent Element</span></span>

## <a name="syntax"></a><span data-ttu-id="0a3fd-106">語法</span><span class="sxs-lookup"><span data-stu-id="0a3fd-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0a3fd-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="0a3fd-107">Attributes and Elements</span></span>

<span data-ttu-id="0a3fd-108">下列各節說明屬性、 子項目和父項目`FirstLineIndent`項目。</span><span class="sxs-lookup"><span data-stu-id="0a3fd-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0a3fd-109">屬性</span><span class="sxs-lookup"><span data-stu-id="0a3fd-109">Attributes</span></span>

<span data-ttu-id="0a3fd-110">無。</span><span class="sxs-lookup"><span data-stu-id="0a3fd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0a3fd-111">子元素</span><span class="sxs-lookup"><span data-stu-id="0a3fd-111">Child Elements</span></span>

<span data-ttu-id="0a3fd-112">無。</span><span class="sxs-lookup"><span data-stu-id="0a3fd-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0a3fd-113">父元素</span><span class="sxs-lookup"><span data-stu-id="0a3fd-113">Parent Elements</span></span>

|<span data-ttu-id="0a3fd-114">元素</span><span class="sxs-lookup"><span data-stu-id="0a3fd-114">Element</span></span>|<span data-ttu-id="0a3fd-115">描述</span><span class="sxs-lookup"><span data-stu-id="0a3fd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0a3fd-116">CustomControl 檢視 （格式） 的 CustomItem 的框架項目</span><span class="sxs-lookup"><span data-stu-id="0a3fd-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="0a3fd-117">定義資料的顯示方式，例如將資料轉移至左邊或右邊。</span><span class="sxs-lookup"><span data-stu-id="0a3fd-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0a3fd-118">文字值</span><span class="sxs-lookup"><span data-stu-id="0a3fd-118">Text Value</span></span>

<span data-ttu-id="0a3fd-119">指定您想要移動資料的第一行的字元數。</span><span class="sxs-lookup"><span data-stu-id="0a3fd-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="0a3fd-120">備註</span><span class="sxs-lookup"><span data-stu-id="0a3fd-120">Remarks</span></span>

<span data-ttu-id="0a3fd-121">如果未指定這個項目，您無法指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)項目。</span><span class="sxs-lookup"><span data-stu-id="0a3fd-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a3fd-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a3fd-122">See Also</span></span>

[<span data-ttu-id="0a3fd-123">FirstLineHanging CustomControl 檢視 （格式） 的畫面格的項目</span><span class="sxs-lookup"><span data-stu-id="0a3fd-123">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0a3fd-124">CustomControl 檢視 （格式） 的 CustomItem 的框架項目</span><span class="sxs-lookup"><span data-stu-id="0a3fd-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0a3fd-125">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="0a3fd-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
