---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)
description: ListControl 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)
ms.openlocfilehash: 2e8246e3ef2cba38824d8f8004acfffc3236df13
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645565"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="9ab3a-103">ListControl 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9ab3a-103">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="9ab3a-104">指定觸發條件的 .NET 型別。</span><span class="sxs-lookup"><span data-stu-id="9ab3a-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="9ab3a-105">當這個型別存在時，就會使用清單專案。</span><span class="sxs-lookup"><span data-stu-id="9ab3a-105">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="9ab3a-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 元素 (format) ListEntries 元素 for ListControl (Format) ListEntry ListEntries for ListControl for 之 entryselectedby (format) ListEntry for ListControl for SelectionCondition 的之 entryselectedby 專案 (格式) ListControl 的 SelectionCondition 專案之 entryselectedby (格式) </span><span class="sxs-lookup"><span data-stu-id="9ab3a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9ab3a-107">語法</span><span class="sxs-lookup"><span data-stu-id="9ab3a-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9ab3a-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9ab3a-108">Attributes and Elements</span></span>

<span data-ttu-id="9ab3a-109">下列各節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="9ab3a-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9ab3a-110">屬性</span><span class="sxs-lookup"><span data-stu-id="9ab3a-110">Attributes</span></span>

<span data-ttu-id="9ab3a-111">無。</span><span class="sxs-lookup"><span data-stu-id="9ab3a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9ab3a-112">子元素</span><span class="sxs-lookup"><span data-stu-id="9ab3a-112">Child Elements</span></span>

<span data-ttu-id="9ab3a-113">無。</span><span class="sxs-lookup"><span data-stu-id="9ab3a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9ab3a-114">父項目</span><span class="sxs-lookup"><span data-stu-id="9ab3a-114">Parent Elements</span></span>

|<span data-ttu-id="9ab3a-115">元素</span><span class="sxs-lookup"><span data-stu-id="9ab3a-115">Element</span></span>|<span data-ttu-id="9ab3a-116">描述</span><span class="sxs-lookup"><span data-stu-id="9ab3a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9ab3a-117">ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9ab3a-117">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="9ab3a-118">定義必須存在才能使用此清單專案的條件。</span><span class="sxs-lookup"><span data-stu-id="9ab3a-118">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9ab3a-119">文字值</span><span class="sxs-lookup"><span data-stu-id="9ab3a-119">Text Value</span></span>

<span data-ttu-id="9ab3a-120">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。</span><span class="sxs-lookup"><span data-stu-id="9ab3a-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="9ab3a-121">備註</span><span class="sxs-lookup"><span data-stu-id="9ab3a-121">Remarks</span></span>

<span data-ttu-id="9ab3a-122">選取條件可以指定任意數目的 .NET 類型或選取集，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="9ab3a-122">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="9ab3a-123">如需如何使用選取條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="9ab3a-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="9ab3a-124">如需清單視圖之其他元件的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="9ab3a-124">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9ab3a-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ab3a-125">See Also</span></span>

[<span data-ttu-id="9ab3a-126">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="9ab3a-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="9ab3a-127">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="9ab3a-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9ab3a-128">ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9ab3a-128">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="9ab3a-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="9ab3a-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
