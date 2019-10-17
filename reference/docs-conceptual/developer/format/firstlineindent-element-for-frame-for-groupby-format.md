---
title: GroupBy 之框架的 FirstLineIndent 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33be3b9e-53c8-433f-8c11-c65b0d46744c
caps.latest.revision: 6
ms.openlocfilehash: 9ba6fc1b9924a4b0d5b56ee15290a2293217403c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363077"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a><span data-ttu-id="b1cde-102">GroupBy 之框架的 FirstLineIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b1cde-102">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>

<span data-ttu-id="b1cde-103">指定第一行資料向右移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="b1cde-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="b1cde-104">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="b1cde-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="b1cde-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（format） CustomEntries 專案的 groupby （format） CustomControl 元素，適用于的 CustomControl for GroupBy （format） CustomEntry 元素適用于 CustomEntry 之 groupby （格式） CustomItem 元素的 groupby （format） CustomControl 專案（適用于 GroupBy 的框架的 groupby （格式） FirstLineIndent 元素）</span><span class="sxs-lookup"><span data-stu-id="b1cde-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format) FirstLineIndent Element for Frame for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b1cde-106">語法</span><span class="sxs-lookup"><span data-stu-id="b1cde-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b1cde-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="b1cde-107">Attributes and Elements</span></span>

<span data-ttu-id="b1cde-108">下列各節描述 `FirstLineIndent` 元素的屬性、子專案和父元素。</span><span class="sxs-lookup"><span data-stu-id="b1cde-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b1cde-109">屬性</span><span class="sxs-lookup"><span data-stu-id="b1cde-109">Attributes</span></span>

<span data-ttu-id="b1cde-110">無。</span><span class="sxs-lookup"><span data-stu-id="b1cde-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b1cde-111">子元素</span><span class="sxs-lookup"><span data-stu-id="b1cde-111">Child Elements</span></span>

<span data-ttu-id="b1cde-112">無。</span><span class="sxs-lookup"><span data-stu-id="b1cde-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b1cde-113">父元素</span><span class="sxs-lookup"><span data-stu-id="b1cde-113">Parent Elements</span></span>

|<span data-ttu-id="b1cde-114">元素</span><span class="sxs-lookup"><span data-stu-id="b1cde-114">Element</span></span>|<span data-ttu-id="b1cde-115">描述</span><span class="sxs-lookup"><span data-stu-id="b1cde-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b1cde-116">GroupBy 之 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b1cde-116">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="b1cde-117">定義資料的顯示方式，例如將資料向左或向右移位。</span><span class="sxs-lookup"><span data-stu-id="b1cde-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b1cde-118">文字值</span><span class="sxs-lookup"><span data-stu-id="b1cde-118">Text Value</span></span>

<span data-ttu-id="b1cde-119">指定您想要將資料行移到第一行的字元數。</span><span class="sxs-lookup"><span data-stu-id="b1cde-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="b1cde-120">備註</span><span class="sxs-lookup"><span data-stu-id="b1cde-120">Remarks</span></span>

<span data-ttu-id="b1cde-121">如果指定這個元素，您就不能指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="b1cde-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1cde-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1cde-122">See Also</span></span>

[<span data-ttu-id="b1cde-123">GroupBy 之框架的 FirstLineHanging 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b1cde-123">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="b1cde-124">GroupBy 之 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b1cde-124">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="b1cde-125">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="b1cde-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)