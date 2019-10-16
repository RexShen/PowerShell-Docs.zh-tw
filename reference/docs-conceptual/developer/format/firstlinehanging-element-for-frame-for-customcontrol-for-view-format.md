---
title: CustomControl for View 的 Frame 的 FirstLineHanging 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6ac3d86-0529-4b93-9bc7-ee94fcef9618
caps.latest.revision: 8
ms.openlocfilehash: ea43e025f5f653ff000e1d7591b535e73da5c9e5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363157"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="050d7-102">檢視之 CustomControl 的框架的 FirstLineHanging 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="050d7-102">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="050d7-103">指定第一行資料向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="050d7-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="050d7-104">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="050d7-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="050d7-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素（format） CustomEntries 元素，用於 CustomEntry for View （Format） CustomEntries 元素的 CustomControl for view （format） CustomItem 元素CustomEntry for CustomControlView （Format）框架元素，用於 CustomItem 的 CustomControl for View （Format） FirstLineHanging 元素（適用于 CustomControl for View 的 Frame）（格式）</span><span class="sxs-lookup"><span data-stu-id="050d7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="050d7-106">語法</span><span class="sxs-lookup"><span data-stu-id="050d7-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="050d7-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="050d7-107">Attributes and Elements</span></span>

<span data-ttu-id="050d7-108">下列各節描述 `FirstLineHanging` 元素的屬性、子專案和父元素。</span><span class="sxs-lookup"><span data-stu-id="050d7-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="050d7-109">屬性</span><span class="sxs-lookup"><span data-stu-id="050d7-109">Attributes</span></span>

<span data-ttu-id="050d7-110">無。</span><span class="sxs-lookup"><span data-stu-id="050d7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="050d7-111">子元素</span><span class="sxs-lookup"><span data-stu-id="050d7-111">Child Elements</span></span>

<span data-ttu-id="050d7-112">無。</span><span class="sxs-lookup"><span data-stu-id="050d7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="050d7-113">父元素</span><span class="sxs-lookup"><span data-stu-id="050d7-113">Parent Elements</span></span>

|<span data-ttu-id="050d7-114">元素</span><span class="sxs-lookup"><span data-stu-id="050d7-114">Element</span></span>|<span data-ttu-id="050d7-115">描述</span><span class="sxs-lookup"><span data-stu-id="050d7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="050d7-116">適用于 CustomControl for View 的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="050d7-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="050d7-117">定義資料的顯示方式，例如將資料向左或向右移位。</span><span class="sxs-lookup"><span data-stu-id="050d7-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="050d7-118">文字值</span><span class="sxs-lookup"><span data-stu-id="050d7-118">Text Value</span></span>

<span data-ttu-id="050d7-119">指定您想要將資料行移到第一行的字元數。</span><span class="sxs-lookup"><span data-stu-id="050d7-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="050d7-120">備註</span><span class="sxs-lookup"><span data-stu-id="050d7-120">Remarks</span></span>

<span data-ttu-id="050d7-121">如果指定這個元素，您就不能指定[FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="050d7-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="050d7-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="050d7-122">See Also</span></span>

[<span data-ttu-id="050d7-123">CustomControl for View 的 Frame 的 FirstLineIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="050d7-123">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="050d7-124">適用于 CustomControl for View 的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="050d7-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="050d7-125">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="050d7-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
