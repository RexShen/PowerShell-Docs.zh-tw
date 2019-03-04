---
title: AutoSize WideControl （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857084"
---
# <a name="autosize-element-for-widecontrol-format"></a><span data-ttu-id="2de31-102">WideControl 的 AutoSize 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2de31-102">AutoSize Element for WideControl (Format)</span></span>

<span data-ttu-id="2de31-103">指定是否資料行大小和資料行數目根據調整大小的資料大小。</span><span class="sxs-lookup"><span data-stu-id="2de31-103">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>

<span data-ttu-id="2de31-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） 自動調整項目 WideControl （格式）</span><span class="sxs-lookup"><span data-stu-id="2de31-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) Autosize Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2de31-105">語法</span><span class="sxs-lookup"><span data-stu-id="2de31-105">Syntax</span></span>

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2de31-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="2de31-106">Attributes and Elements</span></span>

<span data-ttu-id="2de31-107">下列各節說明屬性、 子項目和父項目`AutoSize`項目。</span><span class="sxs-lookup"><span data-stu-id="2de31-107">The following sections describe attributes, child elements, and the parent element of the `AutoSize` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2de31-108">屬性</span><span class="sxs-lookup"><span data-stu-id="2de31-108">Attributes</span></span>

<span data-ttu-id="2de31-109">無。</span><span class="sxs-lookup"><span data-stu-id="2de31-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2de31-110">子元素</span><span class="sxs-lookup"><span data-stu-id="2de31-110">Child Elements</span></span>

<span data-ttu-id="2de31-111">無</span><span class="sxs-lookup"><span data-stu-id="2de31-111">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2de31-112">父元素</span><span class="sxs-lookup"><span data-stu-id="2de31-112">Parent Elements</span></span>

|<span data-ttu-id="2de31-113">元素</span><span class="sxs-lookup"><span data-stu-id="2de31-113">Element</span></span>|<span data-ttu-id="2de31-114">描述</span><span class="sxs-lookup"><span data-stu-id="2de31-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2de31-115">WideControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="2de31-115">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="2de31-116">寬 （單一值） 會定義檢視的清單格式。</span><span class="sxs-lookup"><span data-stu-id="2de31-116">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2de31-117">備註</span><span class="sxs-lookup"><span data-stu-id="2de31-117">Remarks</span></span>

<span data-ttu-id="2de31-118">當定義的寬型檢視，您可以加入`AutoSize`項目或[ColumnNumber](./columnnumber-element-for-widecontrol-format.md)項目，但是您無法新增這兩個。</span><span class="sxs-lookup"><span data-stu-id="2de31-118">When defining a wide view, you can add the `AutoSize` element or the [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element, but you cannot add both.</span></span>

<span data-ttu-id="2de31-119">如需詳細的寬型檢視元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="2de31-119">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="2de31-120">如需寬型檢視的範例，請參閱 < [（基本） 的寬型檢視](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="2de31-120">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2de31-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2de31-121">See Also</span></span>

[<span data-ttu-id="2de31-122">ColumnNumber WideControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="2de31-122">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="2de31-123">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="2de31-123">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="2de31-124">WideControl 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="2de31-124">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="2de31-125">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="2de31-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
