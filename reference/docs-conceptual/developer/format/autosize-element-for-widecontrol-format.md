---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl 的 AutoSize 元素 (格式)
description: WideControl 的 AutoSize 元素 (格式)
ms.openlocfilehash: 42dfae337ba8805e1ddcff4269401afdb3e281f6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92650014"
---
# <a name="autosize-element-for-widecontrol-format"></a><span data-ttu-id="55555-103">WideControl 的 AutoSize 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="55555-103">AutoSize Element for WideControl (Format)</span></span>

<span data-ttu-id="55555-104">指定是否根據資料的大小調整資料行大小和資料行數目。</span><span class="sxs-lookup"><span data-stu-id="55555-104">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>

<span data-ttu-id="55555-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) WideControl 元素 (format) WideControl (格式的 Autosize 元素) </span><span class="sxs-lookup"><span data-stu-id="55555-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) Autosize Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="55555-106">語法</span><span class="sxs-lookup"><span data-stu-id="55555-106">Syntax</span></span>

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="55555-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="55555-107">Attributes and Elements</span></span>

<span data-ttu-id="55555-108">下列各節說明屬性、子專案和元素的父元素 `AutoSize` 。</span><span class="sxs-lookup"><span data-stu-id="55555-108">The following sections describe attributes, child elements, and the parent element of the `AutoSize` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="55555-109">屬性</span><span class="sxs-lookup"><span data-stu-id="55555-109">Attributes</span></span>

<span data-ttu-id="55555-110">無。</span><span class="sxs-lookup"><span data-stu-id="55555-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="55555-111">子元素</span><span class="sxs-lookup"><span data-stu-id="55555-111">Child Elements</span></span>

<span data-ttu-id="55555-112">無</span><span class="sxs-lookup"><span data-stu-id="55555-112">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="55555-113">父項目</span><span class="sxs-lookup"><span data-stu-id="55555-113">Parent Elements</span></span>

|<span data-ttu-id="55555-114">元素</span><span class="sxs-lookup"><span data-stu-id="55555-114">Element</span></span>|<span data-ttu-id="55555-115">描述</span><span class="sxs-lookup"><span data-stu-id="55555-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="55555-116">WideControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="55555-116">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="55555-117">為視圖定義寬 (單一值) 清單格式。</span><span class="sxs-lookup"><span data-stu-id="55555-117">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="55555-118">備註</span><span class="sxs-lookup"><span data-stu-id="55555-118">Remarks</span></span>

<span data-ttu-id="55555-119">定義廣泛的視圖時，您可以加入專案 `AutoSize` 或 [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) 專案，但是您無法同時加入這兩個元素。</span><span class="sxs-lookup"><span data-stu-id="55555-119">When defining a wide view, you can add the `AutoSize` element or the [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element, but you cannot add both.</span></span>

<span data-ttu-id="55555-120">如需有關廣泛視圖元件的詳細資訊，請參閱 [建立廣泛的視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="55555-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="55555-121">如需寬視圖的範例，請參閱 [wide (基本) ](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="55555-121">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="55555-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55555-122">See Also</span></span>

[<span data-ttu-id="55555-123">WideControl 的 ColumnNumber 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="55555-123">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="55555-124">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="55555-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="55555-125">WideControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="55555-125">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="55555-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="55555-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
