---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)
description: WideControl 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)
ms.openlocfilehash: af6e4782c345b43e16bce59c333bdaaceba0d845
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645515"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="d2aa6-103">WideControl 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d2aa6-103">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="d2aa6-104">指定觸發條件的 .NET 型別。</span><span class="sxs-lookup"><span data-stu-id="d2aa6-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="d2aa6-105">當這個型別存在時，就會使用定義。</span><span class="sxs-lookup"><span data-stu-id="d2aa6-105">When this type is present, the definition is used.</span></span>

<span data-ttu-id="d2aa6-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 元素 (格式) WideEntries 專案 (格式) WideEntry 專案 (格式) 之 entryselectedby 專案 (格式) 專案 (格式) WideEntry 專案的 SelectionCondition (格式) 之 entryselectedby 專案 WideEntry 的 SelectionCondition 格式</span><span class="sxs-lookup"><span data-stu-id="d2aa6-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d2aa6-107">語法</span><span class="sxs-lookup"><span data-stu-id="d2aa6-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d2aa6-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d2aa6-108">Attributes and Elements</span></span>

<span data-ttu-id="d2aa6-109">下列各節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="d2aa6-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d2aa6-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d2aa6-110">Attributes</span></span>

<span data-ttu-id="d2aa6-111">無。</span><span class="sxs-lookup"><span data-stu-id="d2aa6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d2aa6-112">子元素</span><span class="sxs-lookup"><span data-stu-id="d2aa6-112">Child Elements</span></span>

<span data-ttu-id="d2aa6-113">無。</span><span class="sxs-lookup"><span data-stu-id="d2aa6-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d2aa6-114">父項目</span><span class="sxs-lookup"><span data-stu-id="d2aa6-114">Parent Elements</span></span>

|<span data-ttu-id="d2aa6-115">元素</span><span class="sxs-lookup"><span data-stu-id="d2aa6-115">Element</span></span>|<span data-ttu-id="d2aa6-116">描述</span><span class="sxs-lookup"><span data-stu-id="d2aa6-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d2aa6-117">適用于之 entryselectedby 的 WideEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="d2aa6-117">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="d2aa6-118">定義必須存在才能使用此寬專案的條件。</span><span class="sxs-lookup"><span data-stu-id="d2aa6-118">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d2aa6-119">文字值</span><span class="sxs-lookup"><span data-stu-id="d2aa6-119">Text Value</span></span>

<span data-ttu-id="d2aa6-120">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。</span><span class="sxs-lookup"><span data-stu-id="d2aa6-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="d2aa6-121">備註</span><span class="sxs-lookup"><span data-stu-id="d2aa6-121">Remarks</span></span>

<span data-ttu-id="d2aa6-122">選取條件可以指定 .NET 類型或選取範圍，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="d2aa6-122">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="d2aa6-123">如需如何使用選取條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="d2aa6-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="d2aa6-124">如需更多有關廣泛視圖的元件的詳細資訊，請參閱 [建立廣泛的觀點](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d2aa6-124">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d2aa6-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2aa6-125">See Also</span></span>

[<span data-ttu-id="d2aa6-126">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="d2aa6-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d2aa6-127">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="d2aa6-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d2aa6-128">適用于之 entryselectedby 的 WideEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="d2aa6-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="d2aa6-129">WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d2aa6-129">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="d2aa6-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="d2aa6-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
