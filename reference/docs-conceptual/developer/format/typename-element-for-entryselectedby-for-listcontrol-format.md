---
title: 之 entryselectedby for ListControl (格式的 TypeName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5e7b73db5aa597d96141454008c5c58b1827df24
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780214"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="4e686-102">ListControl 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4e686-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="4e686-103">指定使用此清單視圖專案的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="4e686-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="4e686-104">可以為清單專案指定的類型數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="4e686-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="4e686-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListEntries 專案 (格式) ListEntry 專案 (格式) 之 entryselectedby 元素（ListEntry (格式) TypeName 元素） (</span><span class="sxs-lookup"><span data-stu-id="4e686-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4e686-106">語法</span><span class="sxs-lookup"><span data-stu-id="4e686-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4e686-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4e686-107">Attributes and Elements</span></span>

<span data-ttu-id="4e686-108">下列各節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="4e686-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4e686-109">屬性</span><span class="sxs-lookup"><span data-stu-id="4e686-109">Attributes</span></span>

<span data-ttu-id="4e686-110">無。</span><span class="sxs-lookup"><span data-stu-id="4e686-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4e686-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4e686-111">Child Elements</span></span>

<span data-ttu-id="4e686-112">無。</span><span class="sxs-lookup"><span data-stu-id="4e686-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4e686-113">父項目</span><span class="sxs-lookup"><span data-stu-id="4e686-113">Parent Elements</span></span>

|<span data-ttu-id="4e686-114">元素</span><span class="sxs-lookup"><span data-stu-id="4e686-114">Element</span></span>|<span data-ttu-id="4e686-115">描述</span><span class="sxs-lookup"><span data-stu-id="4e686-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4e686-116">ListEntry (格式的之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="4e686-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="4e686-117">定義使用此清單專案的 .NET 類型，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="4e686-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4e686-118">文字值</span><span class="sxs-lookup"><span data-stu-id="4e686-118">Text Value</span></span>

<span data-ttu-id="4e686-119">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。</span><span class="sxs-lookup"><span data-stu-id="4e686-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="4e686-120">備註</span><span class="sxs-lookup"><span data-stu-id="4e686-120">Remarks</span></span>

<span data-ttu-id="4e686-121">每個清單專案都必須定義至少一個型別名稱、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="4e686-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="4e686-122">如需如何在清單視圖中使用此元素的詳細資訊，請參閱[清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="4e686-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4e686-123">範例</span><span class="sxs-lookup"><span data-stu-id="4e686-123">Example</span></span>

<span data-ttu-id="4e686-124">下列範例示範如何指定清單視圖專案的選擇集。</span><span class="sxs-lookup"><span data-stu-id="4e686-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="4e686-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e686-125">See Also</span></span>

[<span data-ttu-id="4e686-126">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="4e686-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="4e686-127">ListEntry (格式的之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="4e686-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="4e686-128">ListEntry (格式的之 entryselectedby 的 SelectionSetName 元素) </span><span class="sxs-lookup"><span data-stu-id="4e686-128">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="4e686-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="4e686-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
