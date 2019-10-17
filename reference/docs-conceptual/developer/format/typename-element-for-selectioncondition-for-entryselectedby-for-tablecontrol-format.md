---
title: TableControl 之之 entryselectedby 的 SelectionCondition 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361467"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="bb653-102">TableControl 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bb653-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="bb653-103">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="bb653-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="bb653-104">當此型別存在時，就會符合條件，並使用資料表資料列。</span><span class="sxs-lookup"><span data-stu-id="bb653-104">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="bb653-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（格式）之 entryselectedby 元素（格式）SelectionCondition for 之 entryselectedby for TableRowEntry 的 TableRowEntry （Format） TypeName 元素之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="bb653-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bb653-106">語法</span><span class="sxs-lookup"><span data-stu-id="bb653-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bb653-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="bb653-107">Attributes and Elements</span></span>

<span data-ttu-id="bb653-108">下列各節說明屬性、子專案，以及 `TypeName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="bb653-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bb653-109">屬性</span><span class="sxs-lookup"><span data-stu-id="bb653-109">Attributes</span></span>

<span data-ttu-id="bb653-110">無。</span><span class="sxs-lookup"><span data-stu-id="bb653-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bb653-111">子元素</span><span class="sxs-lookup"><span data-stu-id="bb653-111">Child Elements</span></span>

<span data-ttu-id="bb653-112">無。</span><span class="sxs-lookup"><span data-stu-id="bb653-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bb653-113">父元素</span><span class="sxs-lookup"><span data-stu-id="bb653-113">Parent Elements</span></span>

|<span data-ttu-id="bb653-114">元素</span><span class="sxs-lookup"><span data-stu-id="bb653-114">Element</span></span>|<span data-ttu-id="bb653-115">描述</span><span class="sxs-lookup"><span data-stu-id="bb653-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bb653-116">TableRowEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="bb653-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="bb653-117">定義必須存在才能使用此資料表資料列的條件。</span><span class="sxs-lookup"><span data-stu-id="bb653-117">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bb653-118">文字值</span><span class="sxs-lookup"><span data-stu-id="bb653-118">Text Value</span></span>

<span data-ttu-id="bb653-119">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="bb653-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="bb653-120">備註</span><span class="sxs-lookup"><span data-stu-id="bb653-120">Remarks</span></span>

<span data-ttu-id="bb653-121">選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="bb653-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="bb653-122">如需如何使用選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="bb653-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="bb653-123">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="bb653-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bb653-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb653-124">See Also</span></span>

[<span data-ttu-id="bb653-125">建立資料表視圖</span><span class="sxs-lookup"><span data-stu-id="bb653-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="bb653-126">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="bb653-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="bb653-127">TableRowEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="bb653-127">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="bb653-128">TableRowEntry 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="bb653-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="bb653-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="bb653-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)