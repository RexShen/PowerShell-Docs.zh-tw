---
ms.date: 09/13/2016
ms.topic: reference
title: 展開元素 (格式)
description: 展開元素 (格式)
ms.openlocfilehash: 518e132e3e74b921d4e51966fc60088a22ef63f1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667941"
---
# <a name="expand-element-format"></a><span data-ttu-id="3dd32-103">展開元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3dd32-103">Expand Element (Format)</span></span>

<span data-ttu-id="3dd32-104">指定如何針對此定義展開集合物件。</span><span class="sxs-lookup"><span data-stu-id="3dd32-104">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="3dd32-105">Configuration 元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 元素 (格式)  (展開元素) 格式 (</span><span class="sxs-lookup"><span data-stu-id="3dd32-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3dd32-106">語法</span><span class="sxs-lookup"><span data-stu-id="3dd32-106">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3dd32-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3dd32-107">Attributes and Elements</span></span>

<span data-ttu-id="3dd32-108">下列各節說明屬性、子專案和元素的父元素 `Expand` 。</span><span class="sxs-lookup"><span data-stu-id="3dd32-108">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3dd32-109">屬性</span><span class="sxs-lookup"><span data-stu-id="3dd32-109">Attributes</span></span>

<span data-ttu-id="3dd32-110">無。</span><span class="sxs-lookup"><span data-stu-id="3dd32-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3dd32-111">子元素</span><span class="sxs-lookup"><span data-stu-id="3dd32-111">Child Elements</span></span>

<span data-ttu-id="3dd32-112">無。</span><span class="sxs-lookup"><span data-stu-id="3dd32-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3dd32-113">父項目</span><span class="sxs-lookup"><span data-stu-id="3dd32-113">Parent Elements</span></span>

|<span data-ttu-id="3dd32-114">元素</span><span class="sxs-lookup"><span data-stu-id="3dd32-114">Element</span></span>|<span data-ttu-id="3dd32-115">描述</span><span class="sxs-lookup"><span data-stu-id="3dd32-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3dd32-116">EnumerableExpansion 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3dd32-116">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="3dd32-117">定義當特定 .NET 集合物件顯示在視圖中時，如何展開這些物件。</span><span class="sxs-lookup"><span data-stu-id="3dd32-117">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3dd32-118">文字值</span><span class="sxs-lookup"><span data-stu-id="3dd32-118">Text Value</span></span>

<span data-ttu-id="3dd32-119">指定下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="3dd32-119">Specify one of the following values:</span></span>

- <span data-ttu-id="3dd32-120">EnumOnly：只顯示集合中物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="3dd32-120">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="3dd32-121">CoreOnly：只顯示集合物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="3dd32-121">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="3dd32-122">Both：顯示集合中物件的屬性，以及集合物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="3dd32-122">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="3dd32-123">備註</span><span class="sxs-lookup"><span data-stu-id="3dd32-123">Remarks</span></span>

<span data-ttu-id="3dd32-124">這個元素用來定義集合物件和集合中的物件如何顯示。</span><span class="sxs-lookup"><span data-stu-id="3dd32-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="3dd32-125">在此情況下，集合物件會參考支援  **system.object** 介面的任何物件。</span><span class="sxs-lookup"><span data-stu-id="3dd32-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="3dd32-126">預設行為是只顯示集合中物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="3dd32-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="3dd32-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3dd32-127">See Also</span></span>

[<span data-ttu-id="3dd32-128">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="3dd32-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
