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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862644"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="4218b-102">WideEntry 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4218b-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="4218b-103">指定.NET 型別定義。</span><span class="sxs-lookup"><span data-stu-id="4218b-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="4218b-104">每當此物件會顯示，則會使用定義。</span><span class="sxs-lookup"><span data-stu-id="4218b-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="4218b-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry 項目 （格式） EntrySelectedBy 項目 WideEntry （WideEntry （格式） 類型名稱項目格式）</span><span class="sxs-lookup"><span data-stu-id="4218b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4218b-106">語法</span><span class="sxs-lookup"><span data-stu-id="4218b-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4218b-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="4218b-107">Attributes and Elements</span></span>

<span data-ttu-id="4218b-108">下列各節說明屬性、 子項目和父項目`TypeName`項目。</span><span class="sxs-lookup"><span data-stu-id="4218b-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4218b-109">屬性</span><span class="sxs-lookup"><span data-stu-id="4218b-109">Attributes</span></span>

<span data-ttu-id="4218b-110">無。</span><span class="sxs-lookup"><span data-stu-id="4218b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4218b-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4218b-111">Child Elements</span></span>

<span data-ttu-id="4218b-112">無。</span><span class="sxs-lookup"><span data-stu-id="4218b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4218b-113">父元素</span><span class="sxs-lookup"><span data-stu-id="4218b-113">Parent Elements</span></span>

|<span data-ttu-id="4218b-114">元素</span><span class="sxs-lookup"><span data-stu-id="4218b-114">Element</span></span>|<span data-ttu-id="4218b-115">描述</span><span class="sxs-lookup"><span data-stu-id="4218b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4218b-116">EntrySelectedBy WideEntry （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="4218b-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="4218b-117">定義.NET 型別，使用此寬的項目或要使用此項目必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="4218b-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4218b-118">文字值</span><span class="sxs-lookup"><span data-stu-id="4218b-118">Text Value</span></span>

<span data-ttu-id="4218b-119">指定完整的.NET 型別名稱，例如`System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="4218b-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="4218b-120">備註</span><span class="sxs-lookup"><span data-stu-id="4218b-120">Remarks</span></span>

<span data-ttu-id="4218b-121">一或多個.NET 類型、 選取項目集或選取條件，來定義必須存在，則必須指定每個寬的項目。</span><span class="sxs-lookup"><span data-stu-id="4218b-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="4218b-122">寬型檢視的其他元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="4218b-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4218b-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4218b-123">See Also</span></span>

[<span data-ttu-id="4218b-124">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="4218b-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="4218b-125">EntrySelectedBy WideEntry （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="4218b-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="4218b-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="4218b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
