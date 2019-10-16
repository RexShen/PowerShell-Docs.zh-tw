---
title: 設定之控制項的框架的 FirstLineIndent 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f489720-11f6-4019-940e-07f423d4278d
caps.latest.revision: 6
ms.openlocfilehash: c5b2d971fe1590116f96b024ae8769334768acf2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363117"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="4ebed-102">設定之控制項的框架的 FirstLineIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4ebed-102">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="4ebed-103">指定第一行資料向右移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="4ebed-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="4ebed-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="4ebed-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="4ebed-105">Configuration 元素（格式）控制設定（format） CustomControl 元素的設定（格式）控制項專案的設定專案（格式） CustomControl 設定的 CustomEntries 元素（格式）Format） CustomEntry 元素，用於 CustomControl for 控制項的設定（Format） CustomItem 元素（適用于 CustomItem 的 configuration 框架專案設定的專案，適用于 configuration （格式） FirstLineIndent 元素的 CustomEntry）控制項適用于設定的控制項（格式）</span><span class="sxs-lookup"><span data-stu-id="4ebed-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4ebed-106">語法</span><span class="sxs-lookup"><span data-stu-id="4ebed-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4ebed-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="4ebed-107">Attributes and Elements</span></span>

<span data-ttu-id="4ebed-108">下列各節描述 `FirstLineIndent` 元素的屬性、子專案和父元素。</span><span class="sxs-lookup"><span data-stu-id="4ebed-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4ebed-109">屬性</span><span class="sxs-lookup"><span data-stu-id="4ebed-109">Attributes</span></span>

<span data-ttu-id="4ebed-110">無。</span><span class="sxs-lookup"><span data-stu-id="4ebed-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4ebed-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4ebed-111">Child Elements</span></span>

<span data-ttu-id="4ebed-112">無。</span><span class="sxs-lookup"><span data-stu-id="4ebed-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4ebed-113">父元素</span><span class="sxs-lookup"><span data-stu-id="4ebed-113">Parent Elements</span></span>

|<span data-ttu-id="4ebed-114">元素</span><span class="sxs-lookup"><span data-stu-id="4ebed-114">Element</span></span>|<span data-ttu-id="4ebed-115">描述</span><span class="sxs-lookup"><span data-stu-id="4ebed-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4ebed-116">用於設定之控制項的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4ebed-116">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="4ebed-117">定義資料的顯示方式，例如將資料向左或向右移位。</span><span class="sxs-lookup"><span data-stu-id="4ebed-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4ebed-118">文字值</span><span class="sxs-lookup"><span data-stu-id="4ebed-118">Text Value</span></span>

<span data-ttu-id="4ebed-119">指定您想要將資料行移到第一行的字元數。</span><span class="sxs-lookup"><span data-stu-id="4ebed-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="4ebed-120">備註</span><span class="sxs-lookup"><span data-stu-id="4ebed-120">Remarks</span></span>

<span data-ttu-id="4ebed-121">如果指定這個元素，您就不能指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="4ebed-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ebed-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ebed-122">See Also</span></span>

[<span data-ttu-id="4ebed-123">設定之控制項的框架的 FirstLineHanging 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4ebed-123">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="4ebed-124">用於設定之控制項的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4ebed-124">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="4ebed-125">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="4ebed-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
