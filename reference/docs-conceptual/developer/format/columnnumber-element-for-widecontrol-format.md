---
title: WideControl (格式的 ColumnNumber 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5f151bb0e629efcebe6295cdcae6cebcbbb1b39b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783852"
---
# <a name="columnnumber-element-for-widecontrol-format"></a><span data-ttu-id="03315-102">WideControl 的 ColumnNumber 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="03315-102">ColumnNumber Element for WideControl (Format)</span></span>

<span data-ttu-id="03315-103">指定在寬視圖中顯示的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="03315-103">Specifies the number of columns displayed in the wide view.</span></span>

<span data-ttu-id="03315-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 元素 (格式) WideControl (格式的 ColumnNumber 元素) </span><span class="sxs-lookup"><span data-stu-id="03315-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) ColumnNumber Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="03315-105">語法</span><span class="sxs-lookup"><span data-stu-id="03315-105">Syntax</span></span>

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="03315-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="03315-106">Attributes and Elements</span></span>

<span data-ttu-id="03315-107">下列各節說明屬性、子專案和元素的父元素 `ColumnNumber` 。</span><span class="sxs-lookup"><span data-stu-id="03315-107">The following sections describe attributes, child elements, and the parent element of the `ColumnNumber` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="03315-108">屬性</span><span class="sxs-lookup"><span data-stu-id="03315-108">Attributes</span></span>

<span data-ttu-id="03315-109">無。</span><span class="sxs-lookup"><span data-stu-id="03315-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="03315-110">子元素</span><span class="sxs-lookup"><span data-stu-id="03315-110">Child Elements</span></span>

<span data-ttu-id="03315-111">無。</span><span class="sxs-lookup"><span data-stu-id="03315-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="03315-112">父項目</span><span class="sxs-lookup"><span data-stu-id="03315-112">Parent Elements</span></span>

|<span data-ttu-id="03315-113">元素</span><span class="sxs-lookup"><span data-stu-id="03315-113">Element</span></span>|<span data-ttu-id="03315-114">描述</span><span class="sxs-lookup"><span data-stu-id="03315-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="03315-115">WideControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="03315-115">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="03315-116">定義視圖的寬 (單一值) 清單格式。</span><span class="sxs-lookup"><span data-stu-id="03315-116">Defines a wide (single value) list format for the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="03315-117">文字值</span><span class="sxs-lookup"><span data-stu-id="03315-117">Text Value</span></span>

<span data-ttu-id="03315-118">請指定正整數值。</span><span class="sxs-lookup"><span data-stu-id="03315-118">Specify a positive integer value.</span></span>

## <a name="remarks"></a><span data-ttu-id="03315-119">備註</span><span class="sxs-lookup"><span data-stu-id="03315-119">Remarks</span></span>

<span data-ttu-id="03315-120">定義寬視圖時，您可以加入 `AutoSize` 元素或專案 `ColumnNumber` ，但無法同時新增這兩個專案。</span><span class="sxs-lookup"><span data-stu-id="03315-120">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` element, but you cannot add both.</span></span>

<span data-ttu-id="03315-121">如需有關寬視圖元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="03315-121">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="03315-122">如需寬視圖的範例，請參閱[寬視圖 (基本) ](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="03315-122">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="03315-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03315-123">See Also</span></span>

[<span data-ttu-id="03315-124">WideControl (格式的 Autosize 元素) </span><span class="sxs-lookup"><span data-stu-id="03315-124">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="03315-125">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="03315-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="03315-126">寬型檢視 (基本)</span><span class="sxs-lookup"><span data-stu-id="03315-126">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="03315-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="03315-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
