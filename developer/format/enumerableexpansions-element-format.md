---
title: EnumerableExpansions 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860254"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="d0469-102">EnumerableExpansions 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d0469-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="d0469-103">定義在檢視中顯示時，如何展開.NET 集合物件。</span><span class="sxs-lookup"><span data-stu-id="d0469-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="d0469-104">組態項目 （格式） DefaultSettings 項目 （格式） EnumerableExpansions 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="d0469-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d0469-105">語法</span><span class="sxs-lookup"><span data-stu-id="d0469-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d0469-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="d0469-106">Attributes and Elements</span></span>

<span data-ttu-id="d0469-107">下列各節說明屬性、 子項目和父項目`EnumerableExpansions`項目。</span><span class="sxs-lookup"><span data-stu-id="d0469-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="d0469-108">沒有任何限制，您可以使用的子元素的數目。</span><span class="sxs-lookup"><span data-stu-id="d0469-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="d0469-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d0469-109">Attributes</span></span>

<span data-ttu-id="d0469-110">無。</span><span class="sxs-lookup"><span data-stu-id="d0469-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d0469-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d0469-111">Child Elements</span></span>

|<span data-ttu-id="d0469-112">元素</span><span class="sxs-lookup"><span data-stu-id="d0469-112">Element</span></span>|<span data-ttu-id="d0469-113">描述</span><span class="sxs-lookup"><span data-stu-id="d0469-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0469-114">EnumerableExpansion 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="d0469-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="d0469-115">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="d0469-115">Optional element.</span></span><br /><br /> <span data-ttu-id="d0469-116">定義在檢視中顯示時，會展開的特定.NET 集合物件。</span><span class="sxs-lookup"><span data-stu-id="d0469-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d0469-117">父元素</span><span class="sxs-lookup"><span data-stu-id="d0469-117">Parent Elements</span></span>

|<span data-ttu-id="d0469-118">元素</span><span class="sxs-lookup"><span data-stu-id="d0469-118">Element</span></span>|<span data-ttu-id="d0469-119">描述</span><span class="sxs-lookup"><span data-stu-id="d0469-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0469-120">DefaultSettings 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="d0469-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="d0469-121">定義套用至的格式化檔案的所有檢視的常見設定。</span><span class="sxs-lookup"><span data-stu-id="d0469-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d0469-122">備註</span><span class="sxs-lookup"><span data-stu-id="d0469-122">Remarks</span></span>

<span data-ttu-id="d0469-123">這個項目用來定義集合物件和集合中的物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="d0469-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="d0469-124">集合物件在此情況下，任何支援的物件是指**System.Collections.ICollection**介面。</span><span class="sxs-lookup"><span data-stu-id="d0469-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0469-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0469-125">See Also</span></span>

[<span data-ttu-id="d0469-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="d0469-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
