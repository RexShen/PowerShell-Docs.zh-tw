---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansions 元素 (格式)
description: EnumerableExpansions 元素 (格式)
ms.openlocfilehash: 789599e6ff368b4685c7937d5b6eb38618752f9e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660170"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="97f1b-103">EnumerableExpansions 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="97f1b-103">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="97f1b-104">定義當 .NET 集合物件顯示在視圖中時，如何展開這些物件。</span><span class="sxs-lookup"><span data-stu-id="97f1b-104">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="97f1b-105">Configuration 元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="97f1b-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="97f1b-106">語法</span><span class="sxs-lookup"><span data-stu-id="97f1b-106">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="97f1b-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="97f1b-107">Attributes and Elements</span></span>

<span data-ttu-id="97f1b-108">下列各節說明屬性、子專案和元素的父元素 `EnumerableExpansions` 。</span><span class="sxs-lookup"><span data-stu-id="97f1b-108">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="97f1b-109">您可以使用的子項目數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="97f1b-109">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="97f1b-110">屬性</span><span class="sxs-lookup"><span data-stu-id="97f1b-110">Attributes</span></span>

<span data-ttu-id="97f1b-111">無。</span><span class="sxs-lookup"><span data-stu-id="97f1b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="97f1b-112">子元素</span><span class="sxs-lookup"><span data-stu-id="97f1b-112">Child Elements</span></span>

|<span data-ttu-id="97f1b-113">元素</span><span class="sxs-lookup"><span data-stu-id="97f1b-113">Element</span></span>|<span data-ttu-id="97f1b-114">描述</span><span class="sxs-lookup"><span data-stu-id="97f1b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="97f1b-115">EnumerableExpansion 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="97f1b-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="97f1b-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="97f1b-116">Optional element.</span></span><br /><br /> <span data-ttu-id="97f1b-117">定義特定的 .NET 集合物件，這些物件會在顯示于視圖時展開。</span><span class="sxs-lookup"><span data-stu-id="97f1b-117">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="97f1b-118">父項目</span><span class="sxs-lookup"><span data-stu-id="97f1b-118">Parent Elements</span></span>

|<span data-ttu-id="97f1b-119">元素</span><span class="sxs-lookup"><span data-stu-id="97f1b-119">Element</span></span>|<span data-ttu-id="97f1b-120">描述</span><span class="sxs-lookup"><span data-stu-id="97f1b-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="97f1b-121">DefaultSettings 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="97f1b-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="97f1b-122">定義適用于格式檔案所有視圖的一般設定。</span><span class="sxs-lookup"><span data-stu-id="97f1b-122">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="97f1b-123">備註</span><span class="sxs-lookup"><span data-stu-id="97f1b-123">Remarks</span></span>

<span data-ttu-id="97f1b-124">這個元素用來定義集合物件和集合中的物件如何顯示。</span><span class="sxs-lookup"><span data-stu-id="97f1b-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="97f1b-125">在此情況下，集合物件會參考支援  **system.object** 介面的任何物件。</span><span class="sxs-lookup"><span data-stu-id="97f1b-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="97f1b-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97f1b-126">See Also</span></span>

[<span data-ttu-id="97f1b-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="97f1b-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
