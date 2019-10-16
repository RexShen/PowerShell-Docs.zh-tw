---
title: View 之控制項的框架的 FirstLineHanging 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53694f08-57f7-4185-b443-1636a0918afc
caps.latest.revision: 8
ms.openlocfilehash: 387340cd9b0aae2ad0419b187d96ab4fee183d5a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363787"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-view-format"></a><span data-ttu-id="01742-102">檢視之控制項的框架的 FirstLineHanging 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="01742-102">FirstLineHanging Element for Frame for Controls for View (Format)</span></span>

<span data-ttu-id="01742-103">指定第一行資料向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="01742-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="01742-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="01742-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="01742-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素CustomControl for View （format） CustomEntry 元素，用於 CustomEntries 的 view （format） CustomItem 元素，適用于 CustomEntry for view （format） CustomItem 元素的 view （format） Frame 元素View 控制項的框架（格式）</span><span class="sxs-lookup"><span data-stu-id="01742-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format) FirstLineHanging Element of Frame of Controls of View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="01742-106">語法</span><span class="sxs-lookup"><span data-stu-id="01742-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="01742-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="01742-107">Attributes and Elements</span></span>

<span data-ttu-id="01742-108">下列各節描述 `FirstLineHanging` 元素的屬性、子專案和父元素。</span><span class="sxs-lookup"><span data-stu-id="01742-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="01742-109">屬性</span><span class="sxs-lookup"><span data-stu-id="01742-109">Attributes</span></span>

<span data-ttu-id="01742-110">無。</span><span class="sxs-lookup"><span data-stu-id="01742-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="01742-111">子元素</span><span class="sxs-lookup"><span data-stu-id="01742-111">Child Elements</span></span>

<span data-ttu-id="01742-112">無。</span><span class="sxs-lookup"><span data-stu-id="01742-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="01742-113">父元素</span><span class="sxs-lookup"><span data-stu-id="01742-113">Parent Elements</span></span>

|<span data-ttu-id="01742-114">元素</span><span class="sxs-lookup"><span data-stu-id="01742-114">Element</span></span>|<span data-ttu-id="01742-115">描述</span><span class="sxs-lookup"><span data-stu-id="01742-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="01742-116">View 之控制項的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="01742-116">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="01742-117">定義資料的顯示方式，例如將資料向左或向右移位。</span><span class="sxs-lookup"><span data-stu-id="01742-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="01742-118">文字值</span><span class="sxs-lookup"><span data-stu-id="01742-118">Text Value</span></span>

<span data-ttu-id="01742-119">指定您想要將資料行移到第一行的字元數。</span><span class="sxs-lookup"><span data-stu-id="01742-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="01742-120">備註</span><span class="sxs-lookup"><span data-stu-id="01742-120">Remarks</span></span>

<span data-ttu-id="01742-121">如果指定這個元素，您就不能指定[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="01742-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="01742-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01742-122">See Also</span></span>

[<span data-ttu-id="01742-123">View 之控制項的框架的 FirstLineIndent 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="01742-123">FirstLineIndent Element for Frame for Controls for View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="01742-124">View 之控制項的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="01742-124">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="01742-125">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="01742-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
