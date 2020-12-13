---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)
description: TableControl 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)
ms.openlocfilehash: a984bda6b8fba3a5cb9485576ffd847f0d366d3e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659890"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="1fc3d-103">TableControl 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1fc3d-103">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="1fc3d-104">指定觸發條件的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="1fc3d-104">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="1fc3d-105">當此腳本評估為時 `true` ，就會符合條件，並且會使用資料表專案。</span><span class="sxs-lookup"><span data-stu-id="1fc3d-105">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="1fc3d-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) TableRowEntries 元素 (格式) TableRowEntry 專案 (格式) 之 entryselectedby 專案 (格式) 專案 (格式) TableRowEntry 專案的 SelectionCondition (格式) 之 entryselectedby for TableRowEntry 的 SelectionCondition 格式之 entryselectedby 元素</span><span class="sxs-lookup"><span data-stu-id="1fc3d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1fc3d-107">語法</span><span class="sxs-lookup"><span data-stu-id="1fc3d-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1fc3d-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1fc3d-108">Attributes and Elements</span></span>

<span data-ttu-id="1fc3d-109">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="1fc3d-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1fc3d-110">屬性</span><span class="sxs-lookup"><span data-stu-id="1fc3d-110">Attributes</span></span>

<span data-ttu-id="1fc3d-111">無。</span><span class="sxs-lookup"><span data-stu-id="1fc3d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1fc3d-112">子元素</span><span class="sxs-lookup"><span data-stu-id="1fc3d-112">Child Elements</span></span>

<span data-ttu-id="1fc3d-113">無。</span><span class="sxs-lookup"><span data-stu-id="1fc3d-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1fc3d-114">父項目</span><span class="sxs-lookup"><span data-stu-id="1fc3d-114">Parent Elements</span></span>

|<span data-ttu-id="1fc3d-115">元素</span><span class="sxs-lookup"><span data-stu-id="1fc3d-115">Element</span></span>|<span data-ttu-id="1fc3d-116">描述</span><span class="sxs-lookup"><span data-stu-id="1fc3d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1fc3d-117">適用于之 entryselectedby 的 TableRowEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="1fc3d-117">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="1fc3d-118">定義必須存在才能使用此資料表專案的條件。</span><span class="sxs-lookup"><span data-stu-id="1fc3d-118">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1fc3d-119">文字值</span><span class="sxs-lookup"><span data-stu-id="1fc3d-119">Text Value</span></span>

<span data-ttu-id="1fc3d-120">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="1fc3d-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="1fc3d-121">備註</span><span class="sxs-lookup"><span data-stu-id="1fc3d-121">Remarks</span></span>

<span data-ttu-id="1fc3d-122">選取條件必須指定至少一個腳本區塊或屬性名稱，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="1fc3d-122">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="1fc3d-123">如需如何使用選取條件的詳細資訊，請參閱 [定義使用視圖專案或專案的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="1fc3d-123">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1fc3d-124">如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="1fc3d-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1fc3d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fc3d-125">See Also</span></span>

[<span data-ttu-id="1fc3d-126">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="1fc3d-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="1fc3d-127">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="1fc3d-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1fc3d-128">TableRowEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1fc3d-128">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="1fc3d-129">適用于之 entryselectedby 的 TableRowEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="1fc3d-129">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="1fc3d-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="1fc3d-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
