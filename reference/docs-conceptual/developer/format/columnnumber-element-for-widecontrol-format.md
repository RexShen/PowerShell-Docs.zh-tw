---
title: WideControl 的 ColumnNumber 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364217"
---
# <a name="columnnumber-element-for-widecontrol-format"></a><span data-ttu-id="16efd-102">WideControl 的 ColumnNumber 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="16efd-102">ColumnNumber Element for WideControl (Format)</span></span>

<span data-ttu-id="16efd-103">指定在寬視圖中顯示的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="16efd-103">Specifies the number of columns displayed in the wide view.</span></span>

<span data-ttu-id="16efd-104">WideControl （格式）的設定元素（格式） ViewDefinitions 元素（格式） WideControl 元素（格式） ColumnNumber 元素</span><span class="sxs-lookup"><span data-stu-id="16efd-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) ColumnNumber Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="16efd-105">語法</span><span class="sxs-lookup"><span data-stu-id="16efd-105">Syntax</span></span>

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="16efd-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="16efd-106">Attributes and Elements</span></span>

<span data-ttu-id="16efd-107">下列各節說明屬性、子專案，以及 `ColumnNumber` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="16efd-107">The following sections describe attributes, child elements, and the parent element of the `ColumnNumber` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="16efd-108">屬性</span><span class="sxs-lookup"><span data-stu-id="16efd-108">Attributes</span></span>

<span data-ttu-id="16efd-109">無。</span><span class="sxs-lookup"><span data-stu-id="16efd-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="16efd-110">子元素</span><span class="sxs-lookup"><span data-stu-id="16efd-110">Child Elements</span></span>

<span data-ttu-id="16efd-111">無。</span><span class="sxs-lookup"><span data-stu-id="16efd-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="16efd-112">父元素</span><span class="sxs-lookup"><span data-stu-id="16efd-112">Parent Elements</span></span>

|<span data-ttu-id="16efd-113">元素</span><span class="sxs-lookup"><span data-stu-id="16efd-113">Element</span></span>|<span data-ttu-id="16efd-114">描述</span><span class="sxs-lookup"><span data-stu-id="16efd-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="16efd-115">WideControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="16efd-115">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="16efd-116">定義視圖的寬（單一值）清單格式。</span><span class="sxs-lookup"><span data-stu-id="16efd-116">Defines a wide (single value) list format for the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="16efd-117">文字值</span><span class="sxs-lookup"><span data-stu-id="16efd-117">Text Value</span></span>

<span data-ttu-id="16efd-118">請指定正整數值。</span><span class="sxs-lookup"><span data-stu-id="16efd-118">Specify a positive integer value.</span></span>

## <a name="remarks"></a><span data-ttu-id="16efd-119">備註</span><span class="sxs-lookup"><span data-stu-id="16efd-119">Remarks</span></span>

<span data-ttu-id="16efd-120">定義寬視圖時，您可以加入 `AutoSize` 元素或 @no__t 1 專案，但無法同時新增這兩個元素。</span><span class="sxs-lookup"><span data-stu-id="16efd-120">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` element, but you cannot add both.</span></span>

<span data-ttu-id="16efd-121">如需有關寬視圖元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="16efd-121">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="16efd-122">如需寬視圖的範例，請參閱[寬視圖（基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="16efd-122">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="16efd-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16efd-123">See Also</span></span>

[<span data-ttu-id="16efd-124">WideControl 的 Autosize 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="16efd-124">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="16efd-125">建立寬型視圖</span><span class="sxs-lookup"><span data-stu-id="16efd-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="16efd-126">寬視圖（基本）</span><span class="sxs-lookup"><span data-stu-id="16efd-126">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="16efd-127">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="16efd-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)