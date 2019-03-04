---
title: FirstLineHanging 組態 （格式） 的控制項的畫面格的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 679c8bcb-b49d-4bb4-91f5-ea1af6c217e3
caps.latest.revision: 8
ms.openlocfilehash: 4553f95e48a2b1440c00b4951bea56376b00628a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861334"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="f7681-102">設定之控制項的框架的 FirstLineHanging 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="f7681-102">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="f7681-103">指定資料的第一行向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="f7681-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="f7681-104">定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="f7681-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="f7681-105">組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目CustomControl CustomItem 控制項框架的組態 （格式） FirstLineHanging 項目的組態框架項目控制項的 CustomEntry 的組態 （格式） CustomItem 元素的控制項的格式） CustomEntry 項目組態 （格式） 的控制項</span><span class="sxs-lookup"><span data-stu-id="f7681-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f7681-106">語法</span><span class="sxs-lookup"><span data-stu-id="f7681-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f7681-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="f7681-107">Attributes and Elements</span></span>

<span data-ttu-id="f7681-108">下列各節說明屬性、 子項目和父項目`FirstLineHanging`項目。</span><span class="sxs-lookup"><span data-stu-id="f7681-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f7681-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f7681-109">Attributes</span></span>

<span data-ttu-id="f7681-110">無。</span><span class="sxs-lookup"><span data-stu-id="f7681-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f7681-111">子元素</span><span class="sxs-lookup"><span data-stu-id="f7681-111">Child Elements</span></span>

<span data-ttu-id="f7681-112">無。</span><span class="sxs-lookup"><span data-stu-id="f7681-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f7681-113">父元素</span><span class="sxs-lookup"><span data-stu-id="f7681-113">Parent Elements</span></span>

|<span data-ttu-id="f7681-114">元素</span><span class="sxs-lookup"><span data-stu-id="f7681-114">Element</span></span>|<span data-ttu-id="f7681-115">描述</span><span class="sxs-lookup"><span data-stu-id="f7681-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f7681-116">CustomItem 組態 （格式） 的控制項的框架項目</span><span class="sxs-lookup"><span data-stu-id="f7681-116">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="f7681-117">定義資料的顯示方式，例如將資料轉移至左邊或右邊。</span><span class="sxs-lookup"><span data-stu-id="f7681-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f7681-118">文字值</span><span class="sxs-lookup"><span data-stu-id="f7681-118">Text Value</span></span>

<span data-ttu-id="f7681-119">指定您想要移動資料的第一行的字元數。</span><span class="sxs-lookup"><span data-stu-id="f7681-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="f7681-120">備註</span><span class="sxs-lookup"><span data-stu-id="f7681-120">Remarks</span></span>

<span data-ttu-id="f7681-121">如果未指定這個項目，您不能指定`FirstLineIndent`項目。</span><span class="sxs-lookup"><span data-stu-id="f7681-121">If this element is specified, you cannot specify the `FirstLineIndent` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7681-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7681-122">See Also</span></span>

[<span data-ttu-id="f7681-123">CustomItem 組態 （格式） 的控制項的框架項目</span><span class="sxs-lookup"><span data-stu-id="f7681-123">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="f7681-124">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="f7681-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
