---
title: EnumerableExpansions 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363297"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="f995e-102">EnumerableExpansions 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="f995e-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="f995e-103">定義 .NET 集合物件在視圖中顯示時的展開方式。</span><span class="sxs-lookup"><span data-stu-id="f995e-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="f995e-104">Configuration 元素（格式） DefaultSettings 元素（格式） EnumerableExpansions 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f995e-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f995e-105">語法</span><span class="sxs-lookup"><span data-stu-id="f995e-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f995e-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="f995e-106">Attributes and Elements</span></span>

<span data-ttu-id="f995e-107">下列各節說明屬性、子專案，以及 `EnumerableExpansions` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="f995e-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="f995e-108">您可以使用的子項目數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="f995e-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="f995e-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f995e-109">Attributes</span></span>

<span data-ttu-id="f995e-110">無。</span><span class="sxs-lookup"><span data-stu-id="f995e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f995e-111">子元素</span><span class="sxs-lookup"><span data-stu-id="f995e-111">Child Elements</span></span>

|<span data-ttu-id="f995e-112">元素</span><span class="sxs-lookup"><span data-stu-id="f995e-112">Element</span></span>|<span data-ttu-id="f995e-113">描述</span><span class="sxs-lookup"><span data-stu-id="f995e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f995e-114">EnumerableExpansion 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f995e-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="f995e-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="f995e-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f995e-116">定義在視圖中顯示時展開的特定 .NET 集合物件。</span><span class="sxs-lookup"><span data-stu-id="f995e-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f995e-117">父元素</span><span class="sxs-lookup"><span data-stu-id="f995e-117">Parent Elements</span></span>

|<span data-ttu-id="f995e-118">元素</span><span class="sxs-lookup"><span data-stu-id="f995e-118">Element</span></span>|<span data-ttu-id="f995e-119">描述</span><span class="sxs-lookup"><span data-stu-id="f995e-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f995e-120">DefaultSettings 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f995e-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="f995e-121">定義套用至格式化檔案所有視圖的一般設定。</span><span class="sxs-lookup"><span data-stu-id="f995e-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f995e-122">備註</span><span class="sxs-lookup"><span data-stu-id="f995e-122">Remarks</span></span>

<span data-ttu-id="f995e-123">這個元素是用來定義集合物件和集合中物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="f995e-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="f995e-124">在此情況下，集合物件會參考支援**system.object**介面的任何物件。</span><span class="sxs-lookup"><span data-stu-id="f995e-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="f995e-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f995e-125">See Also</span></span>

[<span data-ttu-id="f995e-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="f995e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
