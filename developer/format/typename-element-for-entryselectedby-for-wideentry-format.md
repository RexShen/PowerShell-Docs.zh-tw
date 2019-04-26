---
title: WideEntry （格式） 的 EntrySelectedBy TypeName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083921"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="d8843-102">WideEntry 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d8843-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="d8843-103">指定.NET 型別定義。</span><span class="sxs-lookup"><span data-stu-id="d8843-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="d8843-104">每當此物件會顯示，則會使用定義。</span><span class="sxs-lookup"><span data-stu-id="d8843-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="d8843-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry 項目 （格式） EntrySelectedBy 項目 WideEntry （WideEntry （格式） 類型名稱項目格式）</span><span class="sxs-lookup"><span data-stu-id="d8843-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d8843-106">語法</span><span class="sxs-lookup"><span data-stu-id="d8843-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d8843-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d8843-107">Attributes and Elements</span></span>

<span data-ttu-id="d8843-108">下列各節說明屬性、 子項目和父項目`TypeName`項目。</span><span class="sxs-lookup"><span data-stu-id="d8843-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d8843-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d8843-109">Attributes</span></span>

<span data-ttu-id="d8843-110">無。</span><span class="sxs-lookup"><span data-stu-id="d8843-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d8843-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d8843-111">Child Elements</span></span>

<span data-ttu-id="d8843-112">無。</span><span class="sxs-lookup"><span data-stu-id="d8843-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d8843-113">父項目</span><span class="sxs-lookup"><span data-stu-id="d8843-113">Parent Elements</span></span>

|<span data-ttu-id="d8843-114">項目</span><span class="sxs-lookup"><span data-stu-id="d8843-114">Element</span></span>|<span data-ttu-id="d8843-115">描述</span><span class="sxs-lookup"><span data-stu-id="d8843-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d8843-116">EntrySelectedBy WideEntry （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="d8843-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="d8843-117">定義.NET 型別，使用此寬的項目或要使用此項目必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="d8843-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d8843-118">文字值</span><span class="sxs-lookup"><span data-stu-id="d8843-118">Text Value</span></span>

<span data-ttu-id="d8843-119">指定完整的.NET 型別名稱，例如`System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="d8843-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="d8843-120">備註</span><span class="sxs-lookup"><span data-stu-id="d8843-120">Remarks</span></span>

<span data-ttu-id="d8843-121">一或多個.NET 類型、 選取項目集或選取條件，來定義必須存在，則必須指定每個寬的項目。</span><span class="sxs-lookup"><span data-stu-id="d8843-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="d8843-122">寬型檢視的其他元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d8843-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d8843-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8843-123">See Also</span></span>

[<span data-ttu-id="d8843-124">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="d8843-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d8843-125">EntrySelectedBy WideEntry （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="d8843-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="d8843-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="d8843-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
