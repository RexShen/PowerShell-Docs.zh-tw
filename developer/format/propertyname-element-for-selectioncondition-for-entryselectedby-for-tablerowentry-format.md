---
title: PropertyName TableRowEntry （格式） 的 EntrySelectedBy 的 SelectionCondition 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064657"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="9f90e-102">TableRowEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9f90e-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="9f90e-103">指定觸發條件的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="9f90e-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="9f90e-104">當這個屬性是存在，或當其評估結果為`true`、 符合條件，並使用資料表項目。</span><span class="sxs-lookup"><span data-stu-id="9f90e-104">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="9f90e-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 （格式） TableRowEntry 項目 （格式） EntrySelectedBy 項目 TableRowEntry （格式）SelectionCondition EntrySelectedBy TableRowEntry （格式） 的 EntrySelectedBy 的 SelectionCondition TableRowEntry （格式） PropertyName 元素的項目</span><span class="sxs-lookup"><span data-stu-id="9f90e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9f90e-106">語法</span><span class="sxs-lookup"><span data-stu-id="9f90e-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9f90e-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9f90e-107">Attributes and Elements</span></span>

<span data-ttu-id="9f90e-108">下列各節說明屬性、 子項目和父項目`PropertyName`項目。</span><span class="sxs-lookup"><span data-stu-id="9f90e-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9f90e-109">屬性</span><span class="sxs-lookup"><span data-stu-id="9f90e-109">Attributes</span></span>

<span data-ttu-id="9f90e-110">無。</span><span class="sxs-lookup"><span data-stu-id="9f90e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9f90e-111">子元素</span><span class="sxs-lookup"><span data-stu-id="9f90e-111">Child Elements</span></span>

<span data-ttu-id="9f90e-112">無。</span><span class="sxs-lookup"><span data-stu-id="9f90e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9f90e-113">父項目</span><span class="sxs-lookup"><span data-stu-id="9f90e-113">Parent Elements</span></span>

|<span data-ttu-id="9f90e-114">項目</span><span class="sxs-lookup"><span data-stu-id="9f90e-114">Element</span></span>|<span data-ttu-id="9f90e-115">描述</span><span class="sxs-lookup"><span data-stu-id="9f90e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9f90e-116">TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="9f90e-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="9f90e-117">定義要使用此資料表項目必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="9f90e-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9f90e-118">文字值</span><span class="sxs-lookup"><span data-stu-id="9f90e-118">Text Value</span></span>

<span data-ttu-id="9f90e-119">指定.NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="9f90e-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="9f90e-120">備註</span><span class="sxs-lookup"><span data-stu-id="9f90e-120">Remarks</span></span>

<span data-ttu-id="9f90e-121">選取條件必須指定至少一個屬性名稱或指令碼區塊，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="9f90e-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="9f90e-122">如需如何使用選擇條件的詳細資訊，請參閱[定義條件時檢視項目或項目用](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="9f90e-122">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="9f90e-123">資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="9f90e-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9f90e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f90e-124">See Also</span></span>

[<span data-ttu-id="9f90e-125">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="9f90e-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="9f90e-126">定義何時顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="9f90e-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9f90e-127">針對 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="9f90e-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="9f90e-128">TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="9f90e-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="9f90e-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="9f90e-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
