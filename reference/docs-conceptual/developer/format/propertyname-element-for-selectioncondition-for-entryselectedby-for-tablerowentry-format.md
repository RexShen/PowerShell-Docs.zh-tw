---
title: TableRowEntry 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364997"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="cffb1-102">TableRowEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="cffb1-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="cffb1-103">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="cffb1-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="cffb1-104">當這個屬性存在或評估為 `true` 時，就會符合條件，並使用資料表專案。</span><span class="sxs-lookup"><span data-stu-id="cffb1-104">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="cffb1-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（格式）之 entryselectedby 元素（格式）SelectionCondition for 之 entryselectedby for TableRowEntry 的 TableRowEntry （Format） PropertyName 元素之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cffb1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cffb1-106">語法</span><span class="sxs-lookup"><span data-stu-id="cffb1-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cffb1-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="cffb1-107">Attributes and Elements</span></span>

<span data-ttu-id="cffb1-108">下列各節說明屬性、子專案，以及 `PropertyName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="cffb1-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cffb1-109">屬性</span><span class="sxs-lookup"><span data-stu-id="cffb1-109">Attributes</span></span>

<span data-ttu-id="cffb1-110">無。</span><span class="sxs-lookup"><span data-stu-id="cffb1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cffb1-111">子元素</span><span class="sxs-lookup"><span data-stu-id="cffb1-111">Child Elements</span></span>

<span data-ttu-id="cffb1-112">無。</span><span class="sxs-lookup"><span data-stu-id="cffb1-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cffb1-113">父元素</span><span class="sxs-lookup"><span data-stu-id="cffb1-113">Parent Elements</span></span>

|<span data-ttu-id="cffb1-114">元素</span><span class="sxs-lookup"><span data-stu-id="cffb1-114">Element</span></span>|<span data-ttu-id="cffb1-115">描述</span><span class="sxs-lookup"><span data-stu-id="cffb1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cffb1-116">TableRowEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cffb1-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="cffb1-117">定義必須存在才能使用此資料表專案的條件。</span><span class="sxs-lookup"><span data-stu-id="cffb1-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cffb1-118">文字值</span><span class="sxs-lookup"><span data-stu-id="cffb1-118">Text Value</span></span>

<span data-ttu-id="cffb1-119">指定 .NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="cffb1-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="cffb1-120">備註</span><span class="sxs-lookup"><span data-stu-id="cffb1-120">Remarks</span></span>

<span data-ttu-id="cffb1-121">選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="cffb1-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="cffb1-122">如需如何使用選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="cffb1-122">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="cffb1-123">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="cffb1-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cffb1-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cffb1-124">See Also</span></span>

[<span data-ttu-id="cffb1-125">建立資料表視圖</span><span class="sxs-lookup"><span data-stu-id="cffb1-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="cffb1-126">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="cffb1-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="cffb1-127">TableRowEntry 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cffb1-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="cffb1-128">TableRowEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cffb1-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="cffb1-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="cffb1-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
