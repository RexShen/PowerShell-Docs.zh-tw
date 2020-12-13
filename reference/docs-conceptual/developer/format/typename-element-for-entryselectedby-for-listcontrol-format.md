---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 EntrySelectedBy 的 TypeName 元素 (格式)
description: ListControl 之 EntrySelectedBy 的 TypeName 元素 (格式)
ms.openlocfilehash: 6fc5a2385fde3140abbc984e3da6a4dda483b2a8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645668"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="80857-103">ListControl 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="80857-103">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="80857-104">指定使用此清單視圖專案的 .NET 型別。</span><span class="sxs-lookup"><span data-stu-id="80857-104">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="80857-105">可以針對清單專案指定的類型數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="80857-105">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="80857-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 專案 (格式) ListEntries 專案 (格式) ListEntry 專案 (格式) 之 entryselectedby 專案的 ListEntry (格式) 之 entryselectedby 的 ListControl (格式) </span><span class="sxs-lookup"><span data-stu-id="80857-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="80857-107">語法</span><span class="sxs-lookup"><span data-stu-id="80857-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="80857-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="80857-108">Attributes and Elements</span></span>

<span data-ttu-id="80857-109">下列各節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="80857-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="80857-110">屬性</span><span class="sxs-lookup"><span data-stu-id="80857-110">Attributes</span></span>

<span data-ttu-id="80857-111">無。</span><span class="sxs-lookup"><span data-stu-id="80857-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="80857-112">子元素</span><span class="sxs-lookup"><span data-stu-id="80857-112">Child Elements</span></span>

<span data-ttu-id="80857-113">無。</span><span class="sxs-lookup"><span data-stu-id="80857-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="80857-114">父項目</span><span class="sxs-lookup"><span data-stu-id="80857-114">Parent Elements</span></span>

|<span data-ttu-id="80857-115">元素</span><span class="sxs-lookup"><span data-stu-id="80857-115">Element</span></span>|<span data-ttu-id="80857-116">描述</span><span class="sxs-lookup"><span data-stu-id="80857-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80857-117">ListEntry (格式的之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="80857-117">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="80857-118">定義使用此清單專案的 .NET 型別，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="80857-118">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="80857-119">文字值</span><span class="sxs-lookup"><span data-stu-id="80857-119">Text Value</span></span>

<span data-ttu-id="80857-120">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。</span><span class="sxs-lookup"><span data-stu-id="80857-120">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="80857-121">備註</span><span class="sxs-lookup"><span data-stu-id="80857-121">Remarks</span></span>

<span data-ttu-id="80857-122">每個清單專案都必須定義至少一個類型名稱、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="80857-122">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="80857-123">如需如何在清單視圖中使用這個元素的詳細資訊，請參閱 [清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="80857-123">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="80857-124">範例</span><span class="sxs-lookup"><span data-stu-id="80857-124">Example</span></span>

<span data-ttu-id="80857-125">下列範例示範如何為清單視圖的專案指定選取集。</span><span class="sxs-lookup"><span data-stu-id="80857-125">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="80857-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80857-126">See Also</span></span>

[<span data-ttu-id="80857-127">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="80857-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="80857-128">ListEntry (格式的之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="80857-128">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="80857-129">適用于之 entryselectedby 的 ListEntry (格式的 SelectionSetName 元素) </span><span class="sxs-lookup"><span data-stu-id="80857-129">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="80857-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="80857-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
