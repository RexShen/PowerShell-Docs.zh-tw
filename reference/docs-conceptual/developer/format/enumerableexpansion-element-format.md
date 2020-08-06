---
title: EnumerableExpansion 元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 81a8959c19502a2e56f4cfa48a1e480509d84b6e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774043"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="189dc-102">EnumerableExpansion 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="189dc-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="189dc-103">定義特定 .NET 集合物件在視圖中顯示時的擴充方式。</span><span class="sxs-lookup"><span data-stu-id="189dc-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="189dc-104">Configuration 元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 元素 (格式) EnumerableExpansion 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="189dc-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="189dc-105">語法</span><span class="sxs-lookup"><span data-stu-id="189dc-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="189dc-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="189dc-106">Attributes and Elements</span></span>

<span data-ttu-id="189dc-107">下列各節說明屬性、子專案和元素的父元素 `EnumerableExpansion` 。</span><span class="sxs-lookup"><span data-stu-id="189dc-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="189dc-108">屬性</span><span class="sxs-lookup"><span data-stu-id="189dc-108">Attributes</span></span>

<span data-ttu-id="189dc-109">無。</span><span class="sxs-lookup"><span data-stu-id="189dc-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="189dc-110">子元素</span><span class="sxs-lookup"><span data-stu-id="189dc-110">Child Elements</span></span>

|<span data-ttu-id="189dc-111">元素</span><span class="sxs-lookup"><span data-stu-id="189dc-111">Element</span></span>|<span data-ttu-id="189dc-112">描述</span><span class="sxs-lookup"><span data-stu-id="189dc-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="189dc-113">EnumerableExpansion 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="189dc-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="189dc-114">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="189dc-114">Optional element.</span></span><br /><br /> <span data-ttu-id="189dc-115">定義由這個定義擴充的 .NET 集合物件。</span><span class="sxs-lookup"><span data-stu-id="189dc-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="189dc-116">展開元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="189dc-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="189dc-117">指定如何展開這個定義的集合物件。</span><span class="sxs-lookup"><span data-stu-id="189dc-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="189dc-118">父項目</span><span class="sxs-lookup"><span data-stu-id="189dc-118">Parent Elements</span></span>

|<span data-ttu-id="189dc-119">元素</span><span class="sxs-lookup"><span data-stu-id="189dc-119">Element</span></span>|<span data-ttu-id="189dc-120">描述</span><span class="sxs-lookup"><span data-stu-id="189dc-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="189dc-121">EnumerableExpansions 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="189dc-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="189dc-122">定義當 .NET 集合物件顯示在視圖中時，所展開的不同方式。</span><span class="sxs-lookup"><span data-stu-id="189dc-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="189dc-123">備註</span><span class="sxs-lookup"><span data-stu-id="189dc-123">Remarks</span></span>

<span data-ttu-id="189dc-124">這個元素是用來定義集合物件和集合中物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="189dc-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="189dc-125">在此情況下，集合物件會參考支援**system.object**介面的任何物件。</span><span class="sxs-lookup"><span data-stu-id="189dc-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="189dc-126">預設行為是只顯示集合中物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="189dc-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="189dc-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="189dc-127">See Also</span></span>

[<span data-ttu-id="189dc-128">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="189dc-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
