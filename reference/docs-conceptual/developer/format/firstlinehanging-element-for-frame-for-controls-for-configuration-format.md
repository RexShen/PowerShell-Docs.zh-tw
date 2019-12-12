---
title: 設定之控制項的框架的 FirstLineHanging 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 679c8bcb-b49d-4bb4-91f5-ea1af6c217e3
caps.latest.revision: 8
ms.openlocfilehash: 4553f95e48a2b1440c00b4951bea56376b00628a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363167"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="29090-102">設定之控制項的框架的 FirstLineHanging 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="29090-102">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="29090-103">指定第一行資料向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="29090-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="29090-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="29090-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="29090-105">Configuration 元素（格式）控制設定（format） CustomControl 元素的設定（格式）控制項專案的設定專案（格式） CustomControl 設定的 CustomEntries 元素（格式）Format） CustomEntry 元素，用於 CustomControl for 控制項的設定（Format） CustomItem 元素（適用于 CustomItem 的 configuration 框架專案設定的專案，適用于 configuration （格式） FirstLineHanging 元素的 CustomEntry）控制項適用于設定的控制項（格式）</span><span class="sxs-lookup"><span data-stu-id="29090-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="29090-106">語法</span><span class="sxs-lookup"><span data-stu-id="29090-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="29090-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="29090-107">Attributes and Elements</span></span>

<span data-ttu-id="29090-108">下列各節描述 `FirstLineHanging` 元素的屬性、子專案和父項目。</span><span class="sxs-lookup"><span data-stu-id="29090-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="29090-109">屬性</span><span class="sxs-lookup"><span data-stu-id="29090-109">Attributes</span></span>

<span data-ttu-id="29090-110">無。</span><span class="sxs-lookup"><span data-stu-id="29090-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="29090-111">子元素</span><span class="sxs-lookup"><span data-stu-id="29090-111">Child Elements</span></span>

<span data-ttu-id="29090-112">無。</span><span class="sxs-lookup"><span data-stu-id="29090-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="29090-113">父元素</span><span class="sxs-lookup"><span data-stu-id="29090-113">Parent Elements</span></span>

|<span data-ttu-id="29090-114">元素</span><span class="sxs-lookup"><span data-stu-id="29090-114">Element</span></span>|<span data-ttu-id="29090-115">描述</span><span class="sxs-lookup"><span data-stu-id="29090-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="29090-116">用於設定之控制項的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="29090-116">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="29090-117">定義資料的顯示方式，例如將資料向左或向右移位。</span><span class="sxs-lookup"><span data-stu-id="29090-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="29090-118">文字值</span><span class="sxs-lookup"><span data-stu-id="29090-118">Text Value</span></span>

<span data-ttu-id="29090-119">指定您想要將資料行移到第一行的字元數。</span><span class="sxs-lookup"><span data-stu-id="29090-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="29090-120">備註</span><span class="sxs-lookup"><span data-stu-id="29090-120">Remarks</span></span>

<span data-ttu-id="29090-121">如果指定這個元素，您就無法指定 `FirstLineIndent` 元素。</span><span class="sxs-lookup"><span data-stu-id="29090-121">If this element is specified, you cannot specify the `FirstLineIndent` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="29090-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29090-122">See Also</span></span>

[<span data-ttu-id="29090-123">用於設定之控制項的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="29090-123">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="29090-124">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="29090-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
