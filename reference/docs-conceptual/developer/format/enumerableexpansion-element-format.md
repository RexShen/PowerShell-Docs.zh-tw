---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansion 元素 (格式)
description: EnumerableExpansion 元素 (格式)
ms.openlocfilehash: 207ad99d5335e99701660159ab77279b55b0b6b5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668009"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="dc37b-103">EnumerableExpansion 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dc37b-103">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="dc37b-104">定義當特定 .NET 集合物件顯示在視圖中時，如何展開這些物件。</span><span class="sxs-lookup"><span data-stu-id="dc37b-104">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="dc37b-105">Configuration 元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 元素 (格式) EnumerableExpansion 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="dc37b-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dc37b-106">語法</span><span class="sxs-lookup"><span data-stu-id="dc37b-106">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dc37b-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dc37b-107">Attributes and Elements</span></span>

<span data-ttu-id="dc37b-108">下列各節說明屬性、子專案和元素的父元素 `EnumerableExpansion` 。</span><span class="sxs-lookup"><span data-stu-id="dc37b-108">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dc37b-109">屬性</span><span class="sxs-lookup"><span data-stu-id="dc37b-109">Attributes</span></span>

<span data-ttu-id="dc37b-110">無。</span><span class="sxs-lookup"><span data-stu-id="dc37b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dc37b-111">子元素</span><span class="sxs-lookup"><span data-stu-id="dc37b-111">Child Elements</span></span>

|<span data-ttu-id="dc37b-112">元素</span><span class="sxs-lookup"><span data-stu-id="dc37b-112">Element</span></span>|<span data-ttu-id="dc37b-113">描述</span><span class="sxs-lookup"><span data-stu-id="dc37b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dc37b-114">EnumerableExpansion 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dc37b-114">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="dc37b-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="dc37b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="dc37b-116">定義由這個定義擴充的 .NET 集合物件。</span><span class="sxs-lookup"><span data-stu-id="dc37b-116">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="dc37b-117">展開元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dc37b-117">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="dc37b-118">指定如何針對此定義展開集合物件。</span><span class="sxs-lookup"><span data-stu-id="dc37b-118">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dc37b-119">父項目</span><span class="sxs-lookup"><span data-stu-id="dc37b-119">Parent Elements</span></span>

|<span data-ttu-id="dc37b-120">元素</span><span class="sxs-lookup"><span data-stu-id="dc37b-120">Element</span></span>|<span data-ttu-id="dc37b-121">描述</span><span class="sxs-lookup"><span data-stu-id="dc37b-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dc37b-122">EnumerableExpansions 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dc37b-122">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="dc37b-123">定義在顯示于視圖中時，.NET 集合物件展開的不同方式。</span><span class="sxs-lookup"><span data-stu-id="dc37b-123">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dc37b-124">備註</span><span class="sxs-lookup"><span data-stu-id="dc37b-124">Remarks</span></span>

<span data-ttu-id="dc37b-125">這個元素用來定義集合物件和集合中的物件如何顯示。</span><span class="sxs-lookup"><span data-stu-id="dc37b-125">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="dc37b-126">在此情況下，集合物件會參考支援  **system.object** 介面的任何物件。</span><span class="sxs-lookup"><span data-stu-id="dc37b-126">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="dc37b-127">預設行為是只顯示集合中物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="dc37b-127">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc37b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc37b-128">See Also</span></span>

[<span data-ttu-id="dc37b-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="dc37b-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
