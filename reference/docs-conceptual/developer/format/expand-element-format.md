---
title: 展開元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: deee832254bb8a774ee2c1f5bd451d3ced1bd47a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783648"
---
# <a name="expand-element-format"></a><span data-ttu-id="ab2bd-102">展開元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ab2bd-102">Expand Element (Format)</span></span>

<span data-ttu-id="ab2bd-103">指定如何展開這個定義的集合物件。</span><span class="sxs-lookup"><span data-stu-id="ab2bd-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="ab2bd-104">Configuration 元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 元素 (格式) EnumerableExpansion 專案 (格式) Expand 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="ab2bd-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ab2bd-105">語法</span><span class="sxs-lookup"><span data-stu-id="ab2bd-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ab2bd-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ab2bd-106">Attributes and Elements</span></span>

<span data-ttu-id="ab2bd-107">下列各節說明屬性、子專案和元素的父元素 `Expand` 。</span><span class="sxs-lookup"><span data-stu-id="ab2bd-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ab2bd-108">屬性</span><span class="sxs-lookup"><span data-stu-id="ab2bd-108">Attributes</span></span>

<span data-ttu-id="ab2bd-109">無。</span><span class="sxs-lookup"><span data-stu-id="ab2bd-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ab2bd-110">子元素</span><span class="sxs-lookup"><span data-stu-id="ab2bd-110">Child Elements</span></span>

<span data-ttu-id="ab2bd-111">無。</span><span class="sxs-lookup"><span data-stu-id="ab2bd-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ab2bd-112">父項目</span><span class="sxs-lookup"><span data-stu-id="ab2bd-112">Parent Elements</span></span>

|<span data-ttu-id="ab2bd-113">元素</span><span class="sxs-lookup"><span data-stu-id="ab2bd-113">Element</span></span>|<span data-ttu-id="ab2bd-114">描述</span><span class="sxs-lookup"><span data-stu-id="ab2bd-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab2bd-115">EnumerableExpansion 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ab2bd-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="ab2bd-116">定義特定 .NET 集合物件在視圖中顯示時的擴充方式。</span><span class="sxs-lookup"><span data-stu-id="ab2bd-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ab2bd-117">文字值</span><span class="sxs-lookup"><span data-stu-id="ab2bd-117">Text Value</span></span>

<span data-ttu-id="ab2bd-118">指定下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="ab2bd-118">Specify one of the following values:</span></span>

- <span data-ttu-id="ab2bd-119">EnumOnly：只顯示集合中物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="ab2bd-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="ab2bd-120">CoreOnly：只顯示集合物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="ab2bd-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="ab2bd-121">Both：顯示集合中物件的屬性，以及集合物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="ab2bd-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="ab2bd-122">備註</span><span class="sxs-lookup"><span data-stu-id="ab2bd-122">Remarks</span></span>

<span data-ttu-id="ab2bd-123">這個元素是用來定義集合物件和集合中物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="ab2bd-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="ab2bd-124">在此情況下，集合物件會參考支援**system.object**介面的任何物件。</span><span class="sxs-lookup"><span data-stu-id="ab2bd-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="ab2bd-125">預設行為是只顯示集合中物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="ab2bd-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab2bd-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab2bd-126">See Also</span></span>

[<span data-ttu-id="ab2bd-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="ab2bd-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
