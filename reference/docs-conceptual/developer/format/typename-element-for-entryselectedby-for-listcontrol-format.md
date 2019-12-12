---
title: ListControl 之之 entryselectedby 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 0f7216d4dcc0380bceb47ea7c15b3d4a7e5ceeb2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361657"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="d302d-102">ListControl 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d302d-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="d302d-103">指定使用此清單視圖專案的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="d302d-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="d302d-104">可以為清單專案指定的類型數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="d302d-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="d302d-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（格式） ListEntries 元素（格式） ListEntry 元素（格式）之 entryselectedby 元素（適用于的 ListEntry （格式） TypeName 元素）ListControl 的之 entryselectedby （格式）</span><span class="sxs-lookup"><span data-stu-id="d302d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d302d-106">語法</span><span class="sxs-lookup"><span data-stu-id="d302d-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d302d-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="d302d-107">Attributes and Elements</span></span>

<span data-ttu-id="d302d-108">下列各節說明屬性、子專案，以及 `TypeName` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="d302d-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d302d-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d302d-109">Attributes</span></span>

<span data-ttu-id="d302d-110">無。</span><span class="sxs-lookup"><span data-stu-id="d302d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d302d-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d302d-111">Child Elements</span></span>

<span data-ttu-id="d302d-112">無。</span><span class="sxs-lookup"><span data-stu-id="d302d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d302d-113">父元素</span><span class="sxs-lookup"><span data-stu-id="d302d-113">Parent Elements</span></span>

|<span data-ttu-id="d302d-114">元素</span><span class="sxs-lookup"><span data-stu-id="d302d-114">Element</span></span>|<span data-ttu-id="d302d-115">描述</span><span class="sxs-lookup"><span data-stu-id="d302d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d302d-116">ListEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d302d-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="d302d-117">定義使用此清單專案的 .NET 類型，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="d302d-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d302d-118">文字值</span><span class="sxs-lookup"><span data-stu-id="d302d-118">Text Value</span></span>

<span data-ttu-id="d302d-119">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="d302d-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="d302d-120">備註</span><span class="sxs-lookup"><span data-stu-id="d302d-120">Remarks</span></span>

<span data-ttu-id="d302d-121">每個清單專案都必須定義至少一個型別名稱、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="d302d-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="d302d-122">如需如何在清單視圖中使用此元素的詳細資訊，請參閱[清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d302d-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d302d-123">範例</span><span class="sxs-lookup"><span data-stu-id="d302d-123">Example</span></span>

<span data-ttu-id="d302d-124">下列範例示範如何指定清單視圖專案的選擇集。</span><span class="sxs-lookup"><span data-stu-id="d302d-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="d302d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d302d-125">See Also</span></span>

[<span data-ttu-id="d302d-126">建立清單視圖</span><span class="sxs-lookup"><span data-stu-id="d302d-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d302d-127">ListEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d302d-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="d302d-128">ListEntry 之之 entryselectedby 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d302d-128">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="d302d-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="d302d-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
