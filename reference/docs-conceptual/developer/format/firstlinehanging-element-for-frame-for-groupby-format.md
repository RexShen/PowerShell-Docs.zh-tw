---
title: GroupBy 之框架的 FirstLineHanging 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363817"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a><span data-ttu-id="df728-102">GroupBy 之框架的 FirstLineHanging 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="df728-102">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>

<span data-ttu-id="df728-103">指定第一行資料向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="df728-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="df728-104">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="df728-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="df728-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（format） CustomEntries 專案的 groupby （format） CustomControl 元素，適用于的 CustomControl for GroupBy （format） CustomEntry 元素適用于 CustomEntry 之 groupby （格式） CustomItem 元素的 groupby （format） CustomControl 專案（適用于 GroupBy 的框架的 groupby （格式） FirstLineHanging 元素）</span><span class="sxs-lookup"><span data-stu-id="df728-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format) FirstLineHanging Element for Frame for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="df728-106">語法</span><span class="sxs-lookup"><span data-stu-id="df728-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="df728-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="df728-107">Attributes and Elements</span></span>

<span data-ttu-id="df728-108">下列各節描述 `FirstLineHanging` 元素的屬性、子專案和父項目。</span><span class="sxs-lookup"><span data-stu-id="df728-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="df728-109">屬性</span><span class="sxs-lookup"><span data-stu-id="df728-109">Attributes</span></span>

<span data-ttu-id="df728-110">無。</span><span class="sxs-lookup"><span data-stu-id="df728-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="df728-111">子元素</span><span class="sxs-lookup"><span data-stu-id="df728-111">Child Elements</span></span>

<span data-ttu-id="df728-112">無。</span><span class="sxs-lookup"><span data-stu-id="df728-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="df728-113">父元素</span><span class="sxs-lookup"><span data-stu-id="df728-113">Parent Elements</span></span>

|<span data-ttu-id="df728-114">元素</span><span class="sxs-lookup"><span data-stu-id="df728-114">Element</span></span>|<span data-ttu-id="df728-115">描述</span><span class="sxs-lookup"><span data-stu-id="df728-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="df728-116">GroupBy 之 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="df728-116">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="df728-117">定義資料的顯示方式，例如將資料向左或向右移位。</span><span class="sxs-lookup"><span data-stu-id="df728-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="df728-118">文字值</span><span class="sxs-lookup"><span data-stu-id="df728-118">Text Value</span></span>

<span data-ttu-id="df728-119">指定您想要將資料行移到第一行的字元數。</span><span class="sxs-lookup"><span data-stu-id="df728-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="df728-120">備註</span><span class="sxs-lookup"><span data-stu-id="df728-120">Remarks</span></span>

<span data-ttu-id="df728-121">如果指定這個元素，您就不能指定[FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="df728-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="df728-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df728-122">See Also</span></span>

[<span data-ttu-id="df728-123">GroupBy 之框架的 FirstLineIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="df728-123">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="df728-124">GroupBy 之 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="df728-124">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="df728-125">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="df728-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
