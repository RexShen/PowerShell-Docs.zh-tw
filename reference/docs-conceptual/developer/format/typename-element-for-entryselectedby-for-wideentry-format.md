---
ms.date: 09/13/2016
ms.topic: reference
title: WideEntry 之 EntrySelectedBy 的 TypeName 元素 (格式)
description: WideEntry 之 EntrySelectedBy 的 TypeName 元素 (格式)
ms.openlocfilehash: 2e0facd6ff7c6fec96dabf488449a8502429bcff
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654785"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="1623a-103">WideEntry 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1623a-103">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="1623a-104">指定定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="1623a-104">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="1623a-105">只要顯示這個物件，就會使用定義。</span><span class="sxs-lookup"><span data-stu-id="1623a-105">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="1623a-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 元素 (格式) WideEntries 元素 (格式) WideEntry 專案 (格式) 之 entryselectedby 專案 (格式)  (格式) 格式的 WideEntry 元素</span><span class="sxs-lookup"><span data-stu-id="1623a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1623a-107">語法</span><span class="sxs-lookup"><span data-stu-id="1623a-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1623a-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1623a-108">Attributes and Elements</span></span>

<span data-ttu-id="1623a-109">下列章節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="1623a-109">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1623a-110">屬性</span><span class="sxs-lookup"><span data-stu-id="1623a-110">Attributes</span></span>

<span data-ttu-id="1623a-111">無。</span><span class="sxs-lookup"><span data-stu-id="1623a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1623a-112">子元素</span><span class="sxs-lookup"><span data-stu-id="1623a-112">Child Elements</span></span>

<span data-ttu-id="1623a-113">無。</span><span class="sxs-lookup"><span data-stu-id="1623a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1623a-114">父項目</span><span class="sxs-lookup"><span data-stu-id="1623a-114">Parent Elements</span></span>

|<span data-ttu-id="1623a-115">元素</span><span class="sxs-lookup"><span data-stu-id="1623a-115">Element</span></span>|<span data-ttu-id="1623a-116">描述</span><span class="sxs-lookup"><span data-stu-id="1623a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1623a-117">WideEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1623a-117">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="1623a-118">定義使用此寬專案的 .NET 型別，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="1623a-118">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1623a-119">文字值</span><span class="sxs-lookup"><span data-stu-id="1623a-119">Text Value</span></span>

<span data-ttu-id="1623a-120">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。</span><span class="sxs-lookup"><span data-stu-id="1623a-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="1623a-121">備註</span><span class="sxs-lookup"><span data-stu-id="1623a-121">Remarks</span></span>

<span data-ttu-id="1623a-122">每個寬專案都必須指定一或多個 .NET 類型、選取集或必須存在的選取條件，才能使用定義。</span><span class="sxs-lookup"><span data-stu-id="1623a-122">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="1623a-123">如需更多有關廣泛視圖的元件的詳細資訊，請參閱 [建立廣泛的觀點](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="1623a-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1623a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1623a-124">See Also</span></span>

[<span data-ttu-id="1623a-125">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="1623a-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="1623a-126">WideEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1623a-126">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="1623a-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="1623a-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
