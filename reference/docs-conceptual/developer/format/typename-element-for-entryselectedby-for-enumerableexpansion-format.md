---
title: EnumerableExpansion 之之 entryselectedby 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0506928-db92-4ec4-855f-6f3592a383ae
caps.latest.revision: 6
ms.openlocfilehash: 5ead806d956ebbef95eeffc42bb39ef784208017
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361747"
---
# <a name="typename-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="37e81-102">EnumerableExpansion 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="37e81-102">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="37e81-103">指定由這個定義擴充的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="37e81-103">Specifies a .NET type that is expanded by this definition.</span></span> <span data-ttu-id="37e81-104">定義預設設定時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="37e81-104">This element is used when defining a default settings.</span></span>

<span data-ttu-id="37e81-105">Configuration 元素（格式） DefaultSettings 元素（格式） EnumerableExpansions 元素（格式） EnumerableExpansion 元素（格式）之 entryselectedby 元素，用於 EnumerableExpansion 的之 entryselectedby （格式） TypeName 元素EnumerableExpansion （格式）</span><span class="sxs-lookup"><span data-stu-id="37e81-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="37e81-106">語法</span><span class="sxs-lookup"><span data-stu-id="37e81-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="37e81-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="37e81-107">Attributes and Elements</span></span>

<span data-ttu-id="37e81-108">下列各節說明屬性、子專案，以及 `TypeName` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="37e81-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="37e81-109">屬性</span><span class="sxs-lookup"><span data-stu-id="37e81-109">Attributes</span></span>

<span data-ttu-id="37e81-110">無。</span><span class="sxs-lookup"><span data-stu-id="37e81-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="37e81-111">子元素</span><span class="sxs-lookup"><span data-stu-id="37e81-111">Child Elements</span></span>

<span data-ttu-id="37e81-112">無。</span><span class="sxs-lookup"><span data-stu-id="37e81-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="37e81-113">父元素</span><span class="sxs-lookup"><span data-stu-id="37e81-113">Parent Elements</span></span>

|<span data-ttu-id="37e81-114">元素</span><span class="sxs-lookup"><span data-stu-id="37e81-114">Element</span></span>|<span data-ttu-id="37e81-115">描述</span><span class="sxs-lookup"><span data-stu-id="37e81-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="37e81-116">EnumerableExpansion 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="37e81-116">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="37e81-117">定義使用此定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="37e81-117">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="37e81-118">文字值</span><span class="sxs-lookup"><span data-stu-id="37e81-118">Text Value</span></span>

<span data-ttu-id="37e81-119">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="37e81-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="37e81-120">備註</span><span class="sxs-lookup"><span data-stu-id="37e81-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="37e81-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37e81-121">See Also</span></span>

[<span data-ttu-id="37e81-122">EnumerableExpansion 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="37e81-122">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="37e81-123">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="37e81-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
