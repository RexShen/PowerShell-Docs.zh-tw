---
title: EnumerableExpansion 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856834"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="901c9-102">EnumerableExpansion 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="901c9-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="901c9-103">定義在檢視中顯示時，會展開物件的特定.NET 集合。</span><span class="sxs-lookup"><span data-stu-id="901c9-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="901c9-104">組態項目 （格式） DefaultSettings 項目 （格式） EnumerableExpansions 項目 （格式） EnumerableExpansion 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="901c9-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="901c9-105">語法</span><span class="sxs-lookup"><span data-stu-id="901c9-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="901c9-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="901c9-106">Attributes and Elements</span></span>

<span data-ttu-id="901c9-107">下列各節說明屬性、 子項目和父項目`EnumerableExpansion`項目。</span><span class="sxs-lookup"><span data-stu-id="901c9-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="901c9-108">屬性</span><span class="sxs-lookup"><span data-stu-id="901c9-108">Attributes</span></span>

<span data-ttu-id="901c9-109">無。</span><span class="sxs-lookup"><span data-stu-id="901c9-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="901c9-110">子元素</span><span class="sxs-lookup"><span data-stu-id="901c9-110">Child Elements</span></span>

|<span data-ttu-id="901c9-111">元素</span><span class="sxs-lookup"><span data-stu-id="901c9-111">Element</span></span>|<span data-ttu-id="901c9-112">描述</span><span class="sxs-lookup"><span data-stu-id="901c9-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="901c9-113">EntrySelectedBy EnumerableExpansion （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="901c9-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="901c9-114">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="901c9-114">Optional element.</span></span><br /><br /> <span data-ttu-id="901c9-115">定義此定義會展開.NET 集合物件。</span><span class="sxs-lookup"><span data-stu-id="901c9-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="901c9-116">展開項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="901c9-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="901c9-117">指定如何展開此定義的集合物件。</span><span class="sxs-lookup"><span data-stu-id="901c9-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="901c9-118">父元素</span><span class="sxs-lookup"><span data-stu-id="901c9-118">Parent Elements</span></span>

|<span data-ttu-id="901c9-119">元素</span><span class="sxs-lookup"><span data-stu-id="901c9-119">Element</span></span>|<span data-ttu-id="901c9-120">描述</span><span class="sxs-lookup"><span data-stu-id="901c9-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="901c9-121">EnumerableExpansions 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="901c9-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="901c9-122">該檢視中顯示時，會展開物件的.NET 集合定義不同的方式。</span><span class="sxs-lookup"><span data-stu-id="901c9-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="901c9-123">備註</span><span class="sxs-lookup"><span data-stu-id="901c9-123">Remarks</span></span>

<span data-ttu-id="901c9-124">這個項目用來定義集合物件和集合中的物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="901c9-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="901c9-125">集合物件在此情況下，任何支援的物件是指**System.Collections.ICollection**介面。</span><span class="sxs-lookup"><span data-stu-id="901c9-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="901c9-126">預設行為是只顯示屬性的物件集合中。</span><span class="sxs-lookup"><span data-stu-id="901c9-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="901c9-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="901c9-127">See Also</span></span>

[<span data-ttu-id="901c9-128">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="901c9-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
