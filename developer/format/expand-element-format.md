---
title: 展開項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066000"
---
# <a name="expand-element-format"></a><span data-ttu-id="8b56d-102">展開元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8b56d-102">Expand Element (Format)</span></span>

<span data-ttu-id="8b56d-103">指定如何展開此定義的集合物件。</span><span class="sxs-lookup"><span data-stu-id="8b56d-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="8b56d-104">組態項目 （格式） DefaultSettings 項目 （格式） EnumerableExpansions 項目 （格式） EnumerableExpansion 項目 （格式） 展開項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="8b56d-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8b56d-105">語法</span><span class="sxs-lookup"><span data-stu-id="8b56d-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8b56d-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8b56d-106">Attributes and Elements</span></span>

<span data-ttu-id="8b56d-107">下列各節說明屬性、 子項目和父項目`Expand`項目。</span><span class="sxs-lookup"><span data-stu-id="8b56d-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8b56d-108">屬性</span><span class="sxs-lookup"><span data-stu-id="8b56d-108">Attributes</span></span>

<span data-ttu-id="8b56d-109">無。</span><span class="sxs-lookup"><span data-stu-id="8b56d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8b56d-110">子元素</span><span class="sxs-lookup"><span data-stu-id="8b56d-110">Child Elements</span></span>

<span data-ttu-id="8b56d-111">無。</span><span class="sxs-lookup"><span data-stu-id="8b56d-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8b56d-112">父項目</span><span class="sxs-lookup"><span data-stu-id="8b56d-112">Parent Elements</span></span>

|<span data-ttu-id="8b56d-113">項目</span><span class="sxs-lookup"><span data-stu-id="8b56d-113">Element</span></span>|<span data-ttu-id="8b56d-114">描述</span><span class="sxs-lookup"><span data-stu-id="8b56d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8b56d-115">EnumerableExpansion 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="8b56d-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="8b56d-116">定義在檢視中顯示時，會展開物件的特定.NET 集合。</span><span class="sxs-lookup"><span data-stu-id="8b56d-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8b56d-117">文字值</span><span class="sxs-lookup"><span data-stu-id="8b56d-117">Text Value</span></span>

<span data-ttu-id="8b56d-118">指定下列值之一：</span><span class="sxs-lookup"><span data-stu-id="8b56d-118">Specify one of the following values:</span></span>

- <span data-ttu-id="8b56d-119">EnumOnly:顯示物件的屬性集合中。</span><span class="sxs-lookup"><span data-stu-id="8b56d-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="8b56d-120">CoreOnly:顯示集合物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="8b56d-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="8b56d-121">兩者：集合和集合物件的屬性中顯示之物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="8b56d-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="8b56d-122">備註</span><span class="sxs-lookup"><span data-stu-id="8b56d-122">Remarks</span></span>

<span data-ttu-id="8b56d-123">這個項目用來定義集合物件和集合中的物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="8b56d-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="8b56d-124">集合物件在此情況下，任何支援的物件是指**System.Collections.ICollection**介面。</span><span class="sxs-lookup"><span data-stu-id="8b56d-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="8b56d-125">預設行為是只顯示屬性的物件集合中。</span><span class="sxs-lookup"><span data-stu-id="8b56d-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b56d-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b56d-126">See Also</span></span>

[<span data-ttu-id="8b56d-127">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="8b56d-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
