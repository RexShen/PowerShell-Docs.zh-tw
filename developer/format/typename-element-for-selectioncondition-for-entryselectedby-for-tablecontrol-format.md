---
title: TableControl （格式） 的 EntrySelectedBy 的 SelectionCondition TypeName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083836"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="e455a-102">TableControl 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e455a-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="e455a-103">指定觸發條件的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="e455a-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="e455a-104">有這種類型時，符合條件，並用資料表資料列。</span><span class="sxs-lookup"><span data-stu-id="e455a-104">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="e455a-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 （格式） TableRowEntry 項目 （格式） EntrySelectedBy 項目 TableRowEntry （格式）SelectionCondition EntrySelectedBy TableRowEntry （格式） 的 EntrySelectedBy 的 SelectionCondition TableRowEntry （格式） 類型名稱元素的項目</span><span class="sxs-lookup"><span data-stu-id="e455a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e455a-106">語法</span><span class="sxs-lookup"><span data-stu-id="e455a-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e455a-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e455a-107">Attributes and Elements</span></span>

<span data-ttu-id="e455a-108">下列各節說明屬性、 子項目和父項目`TypeName`項目。</span><span class="sxs-lookup"><span data-stu-id="e455a-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e455a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="e455a-109">Attributes</span></span>

<span data-ttu-id="e455a-110">無。</span><span class="sxs-lookup"><span data-stu-id="e455a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e455a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="e455a-111">Child Elements</span></span>

<span data-ttu-id="e455a-112">無。</span><span class="sxs-lookup"><span data-stu-id="e455a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e455a-113">父項目</span><span class="sxs-lookup"><span data-stu-id="e455a-113">Parent Elements</span></span>

|<span data-ttu-id="e455a-114">項目</span><span class="sxs-lookup"><span data-stu-id="e455a-114">Element</span></span>|<span data-ttu-id="e455a-115">描述</span><span class="sxs-lookup"><span data-stu-id="e455a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e455a-116">TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="e455a-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="e455a-117">定義必須存在於要使用這個資料表資料列的條件。</span><span class="sxs-lookup"><span data-stu-id="e455a-117">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e455a-118">文字值</span><span class="sxs-lookup"><span data-stu-id="e455a-118">Text Value</span></span>

<span data-ttu-id="e455a-119">指定完整的.NET 型別名稱，例如`System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="e455a-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="e455a-120">備註</span><span class="sxs-lookup"><span data-stu-id="e455a-120">Remarks</span></span>

<span data-ttu-id="e455a-121">選取條件可以指定任意數目的.NET 型別，或選取項目集，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="e455a-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="e455a-122">如需如何使用選擇條件的詳細資訊，請參閱[定義條件時檢視項目或項目用](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e455a-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e455a-123">資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="e455a-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e455a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e455a-124">See Also</span></span>

[<span data-ttu-id="e455a-125">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="e455a-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e455a-126">定義何時顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="e455a-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e455a-127">TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="e455a-127">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e455a-128">針對 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="e455a-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e455a-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="e455a-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
