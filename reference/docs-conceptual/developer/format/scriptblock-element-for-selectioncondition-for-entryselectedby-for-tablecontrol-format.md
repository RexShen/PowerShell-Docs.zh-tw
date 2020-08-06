---
title: SelectionCondition for 之 entryselectedby for TableControl (Format 的 ScriptBlock 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a23d3515749393e9f5a2053634a44d1a817ebf38
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783444"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="bdbe7-102">TableControl 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bdbe7-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="bdbe7-103">指定觸發條件的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="bdbe7-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="bdbe7-104">當此腳本評估為時 `true` ，會符合條件，並使用資料表專案。</span><span class="sxs-lookup"><span data-stu-id="bdbe7-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="bdbe7-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) TableRowEntries 專案 (格式) TableRowEntry 專案 (格式) 之 entryselectedby 元素（TableRowEntry 的 SelectionCondition (格式) 之 entryselectedby 元素，TableRowEntry 適用于 SelectionCondition (格式) </span><span class="sxs-lookup"><span data-stu-id="bdbe7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bdbe7-106">語法</span><span class="sxs-lookup"><span data-stu-id="bdbe7-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bdbe7-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bdbe7-107">Attributes and Elements</span></span>

<span data-ttu-id="bdbe7-108">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="bdbe7-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bdbe7-109">屬性</span><span class="sxs-lookup"><span data-stu-id="bdbe7-109">Attributes</span></span>

<span data-ttu-id="bdbe7-110">無。</span><span class="sxs-lookup"><span data-stu-id="bdbe7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bdbe7-111">子元素</span><span class="sxs-lookup"><span data-stu-id="bdbe7-111">Child Elements</span></span>

<span data-ttu-id="bdbe7-112">無。</span><span class="sxs-lookup"><span data-stu-id="bdbe7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bdbe7-113">父項目</span><span class="sxs-lookup"><span data-stu-id="bdbe7-113">Parent Elements</span></span>

|<span data-ttu-id="bdbe7-114">元素</span><span class="sxs-lookup"><span data-stu-id="bdbe7-114">Element</span></span>|<span data-ttu-id="bdbe7-115">描述</span><span class="sxs-lookup"><span data-stu-id="bdbe7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bdbe7-116">TableRowEntry (格式的之 entryselectedby 的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="bdbe7-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="bdbe7-117">定義必須存在才能使用此資料表專案的條件。</span><span class="sxs-lookup"><span data-stu-id="bdbe7-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bdbe7-118">文字值</span><span class="sxs-lookup"><span data-stu-id="bdbe7-118">Text Value</span></span>

<span data-ttu-id="bdbe7-119">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="bdbe7-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="bdbe7-120">備註</span><span class="sxs-lookup"><span data-stu-id="bdbe7-120">Remarks</span></span>

<span data-ttu-id="bdbe7-121">選取條件必須指定至少一個腳本區塊或屬性名稱，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="bdbe7-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="bdbe7-122">如需如何使用選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="bdbe7-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="bdbe7-123">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="bdbe7-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bdbe7-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdbe7-124">See Also</span></span>

[<span data-ttu-id="bdbe7-125">建立表格檢視</span><span class="sxs-lookup"><span data-stu-id="bdbe7-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="bdbe7-126">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="bdbe7-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="bdbe7-127">TableRowEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bdbe7-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="bdbe7-128">TableRowEntry (格式的之 entryselectedby 的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="bdbe7-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="bdbe7-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="bdbe7-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
