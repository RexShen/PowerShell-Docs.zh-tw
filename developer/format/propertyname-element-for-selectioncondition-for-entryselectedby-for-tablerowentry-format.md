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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860984"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="d24d8-102">TableRowEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d24d8-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="d24d8-103">指定觸發條件的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="d24d8-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="d24d8-104">當這個屬性是存在，或當其評估結果為`true`、 符合條件，並使用資料表項目。</span><span class="sxs-lookup"><span data-stu-id="d24d8-104">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="d24d8-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 （格式） TableRowEntry 項目 （格式） EntrySelectedBy 項目 TableRowEntry （格式）SelectionCondition EntrySelectedBy TableRowEntry （格式） 的 EntrySelectedBy 的 SelectionCondition TableRowEntry （格式） PropertyName 元素的項目</span><span class="sxs-lookup"><span data-stu-id="d24d8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d24d8-106">語法</span><span class="sxs-lookup"><span data-stu-id="d24d8-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d24d8-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="d24d8-107">Attributes and Elements</span></span>

<span data-ttu-id="d24d8-108">下列各節說明屬性、 子項目和父項目`PropertyName`項目。</span><span class="sxs-lookup"><span data-stu-id="d24d8-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d24d8-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d24d8-109">Attributes</span></span>

<span data-ttu-id="d24d8-110">無。</span><span class="sxs-lookup"><span data-stu-id="d24d8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d24d8-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d24d8-111">Child Elements</span></span>

<span data-ttu-id="d24d8-112">無。</span><span class="sxs-lookup"><span data-stu-id="d24d8-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d24d8-113">父元素</span><span class="sxs-lookup"><span data-stu-id="d24d8-113">Parent Elements</span></span>

|<span data-ttu-id="d24d8-114">元素</span><span class="sxs-lookup"><span data-stu-id="d24d8-114">Element</span></span>|<span data-ttu-id="d24d8-115">描述</span><span class="sxs-lookup"><span data-stu-id="d24d8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d24d8-116">TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="d24d8-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="d24d8-117">定義要使用此資料表項目必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="d24d8-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d24d8-118">文字值</span><span class="sxs-lookup"><span data-stu-id="d24d8-118">Text Value</span></span>

<span data-ttu-id="d24d8-119">指定.NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="d24d8-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="d24d8-120">備註</span><span class="sxs-lookup"><span data-stu-id="d24d8-120">Remarks</span></span>

<span data-ttu-id="d24d8-121">選取條件必須指定至少一個屬性名稱或指令碼區塊，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="d24d8-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="d24d8-122">如需如何使用選擇條件的詳細資訊，請參閱[定義條件時檢視項目或項目用](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="d24d8-122">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="d24d8-123">資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d24d8-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d24d8-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d24d8-124">See Also</span></span>

[<span data-ttu-id="d24d8-125">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="d24d8-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d24d8-126">定義何時顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="d24d8-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d24d8-127">針對 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="d24d8-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="d24d8-128">TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="d24d8-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="d24d8-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="d24d8-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
