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
# <a name="columnnumber-element-for-widecontrol-format"></a><span data-ttu-id="3642d-102">WideControl 的 ColumnNumber 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3642d-102">ColumnNumber Element for WideControl (Format)</span></span>

<span data-ttu-id="3642d-103">指定在寬視圖中顯示的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="3642d-103">Specifies the number of columns displayed in the wide view.</span></span>

<span data-ttu-id="3642d-104">WideControl （格式）的設定元素（格式） ViewDefinitions 元素（格式） WideControl 元素（格式） ColumnNumber 元素</span><span class="sxs-lookup"><span data-stu-id="3642d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) ColumnNumber Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3642d-105">語法</span><span class="sxs-lookup"><span data-stu-id="3642d-105">Syntax</span></span>

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3642d-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="3642d-106">Attributes and Elements</span></span>

<span data-ttu-id="3642d-107">下列各節說明屬性、子專案，以及 `ColumnNumber` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="3642d-107">The following sections describe attributes, child elements, and the parent element of the `ColumnNumber` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3642d-108">屬性</span><span class="sxs-lookup"><span data-stu-id="3642d-108">Attributes</span></span>

<span data-ttu-id="3642d-109">無。</span><span class="sxs-lookup"><span data-stu-id="3642d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3642d-110">子元素</span><span class="sxs-lookup"><span data-stu-id="3642d-110">Child Elements</span></span>

<span data-ttu-id="3642d-111">無。</span><span class="sxs-lookup"><span data-stu-id="3642d-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3642d-112">父元素</span><span class="sxs-lookup"><span data-stu-id="3642d-112">Parent Elements</span></span>

|<span data-ttu-id="3642d-113">項目</span><span class="sxs-lookup"><span data-stu-id="3642d-113">Element</span></span>|<span data-ttu-id="3642d-114">說明</span><span class="sxs-lookup"><span data-stu-id="3642d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3642d-115">WideControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3642d-115">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="3642d-116">定義視圖的寬（單一值）清單格式。</span><span class="sxs-lookup"><span data-stu-id="3642d-116">Defines a wide (single value) list format for the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3642d-117">文字值</span><span class="sxs-lookup"><span data-stu-id="3642d-117">Text Value</span></span>

<span data-ttu-id="3642d-118">請指定正整數值。</span><span class="sxs-lookup"><span data-stu-id="3642d-118">Specify a positive integer value.</span></span>

## <a name="remarks"></a><span data-ttu-id="3642d-119">備註</span><span class="sxs-lookup"><span data-stu-id="3642d-119">Remarks</span></span>

<span data-ttu-id="3642d-120">定義寬視圖時，您可以加入 `AutoSize` 元素或 `ColumnNumber` 專案，但無法同時新增兩者。</span><span class="sxs-lookup"><span data-stu-id="3642d-120">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` element, but you cannot add both.</span></span>

<span data-ttu-id="3642d-121">如需有關寬視圖元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="3642d-121">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="3642d-122">如需寬視圖的範例，請參閱[寬視圖（基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="3642d-122">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3642d-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3642d-123">See Also</span></span>

[<span data-ttu-id="3642d-124">WideControl 的 Autosize 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3642d-124">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="3642d-125">建立寬型視圖</span><span class="sxs-lookup"><span data-stu-id="3642d-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="3642d-126">寬視圖（基本）</span><span class="sxs-lookup"><span data-stu-id="3642d-126">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="3642d-127">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="3642d-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
