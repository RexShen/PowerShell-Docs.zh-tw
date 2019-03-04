---
title: ListControl （格式） 的 EntrySelectedBy TypeName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 3f0c0ba1fe85d70557e67a30b3a9a59a33043475
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856104"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="c1c42-102">ListControl 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c1c42-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="c1c42-103">指定使用此項目清單檢視的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="c1c42-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="c1c42-104">類型可指定清單項目數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="c1c42-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="c1c42-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 （格式） ListEntry 項目 （格式） EntrySelectedBy 項目 ListEntry （格式） 類型名稱項目ListControl （格式） 的 EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="c1c42-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c1c42-106">語法</span><span class="sxs-lookup"><span data-stu-id="c1c42-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c1c42-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="c1c42-107">Attributes and Elements</span></span>

<span data-ttu-id="c1c42-108">下列各節說明屬性、 子項目和父項目`TypeName`項目。</span><span class="sxs-lookup"><span data-stu-id="c1c42-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c1c42-109">屬性</span><span class="sxs-lookup"><span data-stu-id="c1c42-109">Attributes</span></span>

<span data-ttu-id="c1c42-110">無。</span><span class="sxs-lookup"><span data-stu-id="c1c42-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c1c42-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c1c42-111">Child Elements</span></span>

<span data-ttu-id="c1c42-112">無。</span><span class="sxs-lookup"><span data-stu-id="c1c42-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c1c42-113">父元素</span><span class="sxs-lookup"><span data-stu-id="c1c42-113">Parent Elements</span></span>

|<span data-ttu-id="c1c42-114">元素</span><span class="sxs-lookup"><span data-stu-id="c1c42-114">Element</span></span>|<span data-ttu-id="c1c42-115">描述</span><span class="sxs-lookup"><span data-stu-id="c1c42-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1c42-116">EntrySelectedBy ListEntry （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="c1c42-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="c1c42-117">定義.NET 型別，使用此清單項目或要使用此項目必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="c1c42-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c1c42-118">文字值</span><span class="sxs-lookup"><span data-stu-id="c1c42-118">Text Value</span></span>

<span data-ttu-id="c1c42-119">指定完整.NET 類型名稱，例如`System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="c1c42-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="c1c42-120">備註</span><span class="sxs-lookup"><span data-stu-id="c1c42-120">Remarks</span></span>

<span data-ttu-id="c1c42-121">每個清單項目必須至少一個型別名稱、 選取項目集或選擇條件的定義。</span><span class="sxs-lookup"><span data-stu-id="c1c42-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="c1c42-122">如需如何使用這個項目在清單檢視中的詳細資訊，請參閱[清單檢視](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="c1c42-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c1c42-123">範例</span><span class="sxs-lookup"><span data-stu-id="c1c42-123">Example</span></span>

<span data-ttu-id="c1c42-124">下列範例示範如何指定設定項目清單檢視的選取範圍。</span><span class="sxs-lookup"><span data-stu-id="c1c42-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="c1c42-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1c42-125">See Also</span></span>

[<span data-ttu-id="c1c42-126">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="c1c42-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c1c42-127">EntrySelectedBy ListEntry （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="c1c42-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="c1c42-128">ListEntry （格式） 的 EnrtySelectedBy SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="c1c42-128">SelectionSetName Element for EnrtySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="c1c42-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="c1c42-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
