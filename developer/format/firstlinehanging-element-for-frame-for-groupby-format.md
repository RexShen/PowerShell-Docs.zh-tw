---
title: GroupBy （格式） 的畫面格 FirstLineHanging 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065819"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a><span data-ttu-id="8cc79-102">GroupBy 之框架的 FirstLineHanging 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8cc79-102">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>

<span data-ttu-id="8cc79-103">指定資料的第一行向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="8cc79-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="8cc79-104">定義新的群組物件的顯示方式時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="8cc79-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="8cc79-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素CustomControl CustomEntry CustomItem 框架 GroupBy （格式） 的 GroupBy （格式） FirstLineHanging 元素的 GroupBy （格式） 框架元素的 GroupBy （格式） CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="8cc79-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format) FirstLineHanging Element for Frame for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8cc79-106">語法</span><span class="sxs-lookup"><span data-stu-id="8cc79-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8cc79-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8cc79-107">Attributes and Elements</span></span>

<span data-ttu-id="8cc79-108">下列各節說明屬性、 子項目和父項目`FirstLineHanging`項目。</span><span class="sxs-lookup"><span data-stu-id="8cc79-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8cc79-109">屬性</span><span class="sxs-lookup"><span data-stu-id="8cc79-109">Attributes</span></span>

<span data-ttu-id="8cc79-110">無。</span><span class="sxs-lookup"><span data-stu-id="8cc79-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8cc79-111">子元素</span><span class="sxs-lookup"><span data-stu-id="8cc79-111">Child Elements</span></span>

<span data-ttu-id="8cc79-112">無。</span><span class="sxs-lookup"><span data-stu-id="8cc79-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8cc79-113">父項目</span><span class="sxs-lookup"><span data-stu-id="8cc79-113">Parent Elements</span></span>

|<span data-ttu-id="8cc79-114">項目</span><span class="sxs-lookup"><span data-stu-id="8cc79-114">Element</span></span>|<span data-ttu-id="8cc79-115">描述</span><span class="sxs-lookup"><span data-stu-id="8cc79-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8cc79-116">GroupBy （格式） 的 CustomItem 的框架項目</span><span class="sxs-lookup"><span data-stu-id="8cc79-116">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="8cc79-117">定義資料的顯示方式，例如將資料轉移至左邊或右邊。</span><span class="sxs-lookup"><span data-stu-id="8cc79-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8cc79-118">文字值</span><span class="sxs-lookup"><span data-stu-id="8cc79-118">Text Value</span></span>

<span data-ttu-id="8cc79-119">指定您想要移動資料的第一行的字元數。</span><span class="sxs-lookup"><span data-stu-id="8cc79-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="8cc79-120">備註</span><span class="sxs-lookup"><span data-stu-id="8cc79-120">Remarks</span></span>

<span data-ttu-id="8cc79-121">如果未指定這個項目，您無法指定[FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md)項目。</span><span class="sxs-lookup"><span data-stu-id="8cc79-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="8cc79-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cc79-122">See Also</span></span>

[<span data-ttu-id="8cc79-123">GroupBy （格式） 的畫面格 FirstLineIndent 項目</span><span class="sxs-lookup"><span data-stu-id="8cc79-123">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="8cc79-124">GroupBy （格式） 的 CustomItem 的框架項目</span><span class="sxs-lookup"><span data-stu-id="8cc79-124">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="8cc79-125">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="8cc79-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
