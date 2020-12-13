---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)
description: TableControl 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)
ms.openlocfilehash: 66e90ab33775cf35d5e98e45266996d2d1a622d7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659639"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="847b3-103">TableControl 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="847b3-103">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="847b3-104">指定觸發條件的 .NET 型別。</span><span class="sxs-lookup"><span data-stu-id="847b3-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="847b3-105">當此類型存在時，就會符合條件，並且會使用資料表資料列。</span><span class="sxs-lookup"><span data-stu-id="847b3-105">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="847b3-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) TableRowEntries 專案 (格式) TableRowEntry 專案 (格式) 之 entryselectedby 專案 (格式) 專案 (格式) TableRowEntry 專案的 SelectionCondition (格式) 之 entryselectedby 專案 TableRowEntry 的 SelectionCondition 格式</span><span class="sxs-lookup"><span data-stu-id="847b3-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="847b3-107">語法</span><span class="sxs-lookup"><span data-stu-id="847b3-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="847b3-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="847b3-108">Attributes and Elements</span></span>

<span data-ttu-id="847b3-109">下列各節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="847b3-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="847b3-110">屬性</span><span class="sxs-lookup"><span data-stu-id="847b3-110">Attributes</span></span>

<span data-ttu-id="847b3-111">無。</span><span class="sxs-lookup"><span data-stu-id="847b3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="847b3-112">子元素</span><span class="sxs-lookup"><span data-stu-id="847b3-112">Child Elements</span></span>

<span data-ttu-id="847b3-113">無。</span><span class="sxs-lookup"><span data-stu-id="847b3-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="847b3-114">父項目</span><span class="sxs-lookup"><span data-stu-id="847b3-114">Parent Elements</span></span>

|<span data-ttu-id="847b3-115">元素</span><span class="sxs-lookup"><span data-stu-id="847b3-115">Element</span></span>|<span data-ttu-id="847b3-116">描述</span><span class="sxs-lookup"><span data-stu-id="847b3-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="847b3-117">適用于之 entryselectedby 的 TableRowEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="847b3-117">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="847b3-118">定義必須存在才能使用此資料表資料列的條件。</span><span class="sxs-lookup"><span data-stu-id="847b3-118">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="847b3-119">文字值</span><span class="sxs-lookup"><span data-stu-id="847b3-119">Text Value</span></span>

<span data-ttu-id="847b3-120">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。</span><span class="sxs-lookup"><span data-stu-id="847b3-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="847b3-121">備註</span><span class="sxs-lookup"><span data-stu-id="847b3-121">Remarks</span></span>

<span data-ttu-id="847b3-122">選取條件可以指定任意數目的 .NET 類型或選取集，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="847b3-122">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="847b3-123">如需如何使用選取條件的詳細資訊，請參閱 [定義使用視圖專案或專案的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="847b3-123">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="847b3-124">如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="847b3-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="847b3-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="847b3-125">See Also</span></span>

[<span data-ttu-id="847b3-126">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="847b3-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="847b3-127">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="847b3-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="847b3-128">適用于之 entryselectedby 的 TableRowEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="847b3-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="847b3-129">適用于 TableRowEntry 的之 entryselectedby (格式的 SelectionCondition SelectionSetName 元素) </span><span class="sxs-lookup"><span data-stu-id="847b3-129">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="847b3-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="847b3-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
