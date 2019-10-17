---
title: 展開元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368737"
---
# <a name="expand-element-format"></a><span data-ttu-id="475ec-102">展開元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="475ec-102">Expand Element (Format)</span></span>

<span data-ttu-id="475ec-103">指定如何展開這個定義的集合物件。</span><span class="sxs-lookup"><span data-stu-id="475ec-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="475ec-104">Configuration 元素（格式） DefaultSettings 元素（格式） EnumerableExpansions 元素（格式） EnumerableExpansion 元素（格式）展開元素（格式）</span><span class="sxs-lookup"><span data-stu-id="475ec-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="475ec-105">語法</span><span class="sxs-lookup"><span data-stu-id="475ec-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="475ec-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="475ec-106">Attributes and Elements</span></span>

<span data-ttu-id="475ec-107">下列各節說明屬性、子專案，以及 `Expand` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="475ec-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="475ec-108">屬性</span><span class="sxs-lookup"><span data-stu-id="475ec-108">Attributes</span></span>

<span data-ttu-id="475ec-109">無。</span><span class="sxs-lookup"><span data-stu-id="475ec-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="475ec-110">子元素</span><span class="sxs-lookup"><span data-stu-id="475ec-110">Child Elements</span></span>

<span data-ttu-id="475ec-111">無。</span><span class="sxs-lookup"><span data-stu-id="475ec-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="475ec-112">父元素</span><span class="sxs-lookup"><span data-stu-id="475ec-112">Parent Elements</span></span>

|<span data-ttu-id="475ec-113">元素</span><span class="sxs-lookup"><span data-stu-id="475ec-113">Element</span></span>|<span data-ttu-id="475ec-114">描述</span><span class="sxs-lookup"><span data-stu-id="475ec-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="475ec-115">EnumerableExpansion 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="475ec-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="475ec-116">定義特定 .NET 集合物件在視圖中顯示時的擴充方式。</span><span class="sxs-lookup"><span data-stu-id="475ec-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="475ec-117">文字值</span><span class="sxs-lookup"><span data-stu-id="475ec-117">Text Value</span></span>

<span data-ttu-id="475ec-118">指定下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="475ec-118">Specify one of the following values:</span></span>

- <span data-ttu-id="475ec-119">EnumOnly：只顯示集合中物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="475ec-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="475ec-120">CoreOnly：只顯示集合物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="475ec-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="475ec-121">Both：顯示集合中物件的屬性，以及集合物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="475ec-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="475ec-122">備註</span><span class="sxs-lookup"><span data-stu-id="475ec-122">Remarks</span></span>

<span data-ttu-id="475ec-123">這個元素是用來定義集合物件和集合中物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="475ec-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="475ec-124">在此情況下，集合物件會參考支援**system.object**介面的任何物件。</span><span class="sxs-lookup"><span data-stu-id="475ec-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="475ec-125">預設行為是只顯示集合中物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="475ec-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="475ec-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="475ec-126">See Also</span></span>

[<span data-ttu-id="475ec-127">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="475ec-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)