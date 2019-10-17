---
title: WideControl 的 AutoSize 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369047"
---
# <a name="autosize-element-for-widecontrol-format"></a><span data-ttu-id="d5c96-102">WideControl 的 AutoSize 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d5c96-102">AutoSize Element for WideControl (Format)</span></span>

<span data-ttu-id="d5c96-103">指定是否根據資料大小來調整資料行大小和資料行數目。</span><span class="sxs-lookup"><span data-stu-id="d5c96-103">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>

<span data-ttu-id="d5c96-104">WideControl 的 Configuration 元素（格式） ViewDefinitions 元素（格式） WideControl 元素（格式） Autosize 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d5c96-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) Autosize Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d5c96-105">語法</span><span class="sxs-lookup"><span data-stu-id="d5c96-105">Syntax</span></span>

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d5c96-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="d5c96-106">Attributes and Elements</span></span>

<span data-ttu-id="d5c96-107">下列各節說明屬性、子專案，以及 `AutoSize` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="d5c96-107">The following sections describe attributes, child elements, and the parent element of the `AutoSize` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d5c96-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d5c96-108">Attributes</span></span>

<span data-ttu-id="d5c96-109">無。</span><span class="sxs-lookup"><span data-stu-id="d5c96-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d5c96-110">子元素</span><span class="sxs-lookup"><span data-stu-id="d5c96-110">Child Elements</span></span>

<span data-ttu-id="d5c96-111">無</span><span class="sxs-lookup"><span data-stu-id="d5c96-111">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d5c96-112">父元素</span><span class="sxs-lookup"><span data-stu-id="d5c96-112">Parent Elements</span></span>

|<span data-ttu-id="d5c96-113">元素</span><span class="sxs-lookup"><span data-stu-id="d5c96-113">Element</span></span>|<span data-ttu-id="d5c96-114">描述</span><span class="sxs-lookup"><span data-stu-id="d5c96-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d5c96-115">WideControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d5c96-115">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="d5c96-116">定義視圖的寬（單一值）清單格式。</span><span class="sxs-lookup"><span data-stu-id="d5c96-116">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d5c96-117">備註</span><span class="sxs-lookup"><span data-stu-id="d5c96-117">Remarks</span></span>

<span data-ttu-id="d5c96-118">定義寬視圖時，您可以加入 `AutoSize` 元素或[ColumnNumber](./columnnumber-element-for-widecontrol-format.md)元素，但無法同時新增這兩個專案。</span><span class="sxs-lookup"><span data-stu-id="d5c96-118">When defining a wide view, you can add the `AutoSize` element or the [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element, but you cannot add both.</span></span>

<span data-ttu-id="d5c96-119">如需有關寬視圖元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d5c96-119">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="d5c96-120">如需寬視圖的範例，請參閱[寬視圖（基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="d5c96-120">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d5c96-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5c96-121">See Also</span></span>

[<span data-ttu-id="d5c96-122">WideControl 的 ColumnNumber 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d5c96-122">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="d5c96-123">建立寬型視圖</span><span class="sxs-lookup"><span data-stu-id="d5c96-123">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d5c96-124">WideControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d5c96-124">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="d5c96-125">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="d5c96-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)