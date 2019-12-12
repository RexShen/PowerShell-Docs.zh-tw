---
title: TableControl 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368577"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="2d5ea-102">TableControl 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2d5ea-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="2d5ea-103">指定觸發條件的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="2d5ea-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="2d5ea-104">當此腳本評估為 `true`時，就會符合條件，並使用資料表專案。</span><span class="sxs-lookup"><span data-stu-id="2d5ea-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="2d5ea-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（格式）之 entryselectedby 元素（格式）SelectionCondition for 之 entryselectedby 之 TableRowEntry 的 TableRowEntry （Format） ScriptBlock 元素之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2d5ea-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2d5ea-106">語法</span><span class="sxs-lookup"><span data-stu-id="2d5ea-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2d5ea-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="2d5ea-107">Attributes and Elements</span></span>

<span data-ttu-id="2d5ea-108">下列各節說明屬性、子專案，以及 `ScriptBlock` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="2d5ea-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2d5ea-109">屬性</span><span class="sxs-lookup"><span data-stu-id="2d5ea-109">Attributes</span></span>

<span data-ttu-id="2d5ea-110">無。</span><span class="sxs-lookup"><span data-stu-id="2d5ea-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2d5ea-111">子元素</span><span class="sxs-lookup"><span data-stu-id="2d5ea-111">Child Elements</span></span>

<span data-ttu-id="2d5ea-112">無。</span><span class="sxs-lookup"><span data-stu-id="2d5ea-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2d5ea-113">父元素</span><span class="sxs-lookup"><span data-stu-id="2d5ea-113">Parent Elements</span></span>

|<span data-ttu-id="2d5ea-114">元素</span><span class="sxs-lookup"><span data-stu-id="2d5ea-114">Element</span></span>|<span data-ttu-id="2d5ea-115">描述</span><span class="sxs-lookup"><span data-stu-id="2d5ea-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2d5ea-116">TableRowEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2d5ea-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="2d5ea-117">定義必須存在才能使用此資料表專案的條件。</span><span class="sxs-lookup"><span data-stu-id="2d5ea-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2d5ea-118">文字值</span><span class="sxs-lookup"><span data-stu-id="2d5ea-118">Text Value</span></span>

<span data-ttu-id="2d5ea-119">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="2d5ea-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="2d5ea-120">備註</span><span class="sxs-lookup"><span data-stu-id="2d5ea-120">Remarks</span></span>

<span data-ttu-id="2d5ea-121">選取條件必須指定至少一個腳本區塊或屬性名稱，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="2d5ea-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="2d5ea-122">如需如何使用選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="2d5ea-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="2d5ea-123">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="2d5ea-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2d5ea-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d5ea-124">See Also</span></span>

[<span data-ttu-id="2d5ea-125">建立資料表視圖</span><span class="sxs-lookup"><span data-stu-id="2d5ea-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2d5ea-126">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="2d5ea-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2d5ea-127">TableRowEntry 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2d5ea-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="2d5ea-128">TableRowEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2d5ea-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="2d5ea-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="2d5ea-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
