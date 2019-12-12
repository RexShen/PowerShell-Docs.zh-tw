---
title: WideEntry 之之 entryselectedby 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361617"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="b6365-102">WideEntry 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b6365-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="b6365-103">指定定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="b6365-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="b6365-104">每當顯示此物件時，就會使用此定義。</span><span class="sxs-lookup"><span data-stu-id="b6365-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="b6365-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（格式）之 entryselectedby 元素（適用于 WideEntry 的 WideEntry （格式） TypeName 元素）編排</span><span class="sxs-lookup"><span data-stu-id="b6365-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b6365-106">語法</span><span class="sxs-lookup"><span data-stu-id="b6365-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b6365-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="b6365-107">Attributes and Elements</span></span>

<span data-ttu-id="b6365-108">下列各節說明屬性、子專案，以及 `TypeName` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="b6365-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b6365-109">屬性</span><span class="sxs-lookup"><span data-stu-id="b6365-109">Attributes</span></span>

<span data-ttu-id="b6365-110">無。</span><span class="sxs-lookup"><span data-stu-id="b6365-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b6365-111">子元素</span><span class="sxs-lookup"><span data-stu-id="b6365-111">Child Elements</span></span>

<span data-ttu-id="b6365-112">無。</span><span class="sxs-lookup"><span data-stu-id="b6365-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b6365-113">父元素</span><span class="sxs-lookup"><span data-stu-id="b6365-113">Parent Elements</span></span>

|<span data-ttu-id="b6365-114">元素</span><span class="sxs-lookup"><span data-stu-id="b6365-114">Element</span></span>|<span data-ttu-id="b6365-115">描述</span><span class="sxs-lookup"><span data-stu-id="b6365-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b6365-116">WideEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b6365-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="b6365-117">定義使用此寬專案的 .NET 類型，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="b6365-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b6365-118">文字值</span><span class="sxs-lookup"><span data-stu-id="b6365-118">Text Value</span></span>

<span data-ttu-id="b6365-119">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="b6365-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="b6365-120">備註</span><span class="sxs-lookup"><span data-stu-id="b6365-120">Remarks</span></span>

<span data-ttu-id="b6365-121">每個寬型別都必須指定一個或多個 .NET 類型、一個選取集，或必須存在才能使用定義的選取條件。</span><span class="sxs-lookup"><span data-stu-id="b6365-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="b6365-122">如需有關寬視圖之其他元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="b6365-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b6365-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6365-123">See Also</span></span>

[<span data-ttu-id="b6365-124">建立寬型視圖</span><span class="sxs-lookup"><span data-stu-id="b6365-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="b6365-125">WideEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b6365-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="b6365-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="b6365-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
