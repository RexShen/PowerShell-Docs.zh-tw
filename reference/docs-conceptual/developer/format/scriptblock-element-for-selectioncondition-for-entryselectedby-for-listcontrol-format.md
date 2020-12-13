---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)
description: ListControl 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)
ms.openlocfilehash: ec7691358d0ff3758411317a349221e1704a1895
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659912"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="80875-103">ListControl 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="80875-103">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="80875-104">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="80875-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="80875-105">當此腳本評估為時 `true` ，就會符合條件，並且會使用清單專案。</span><span class="sxs-lookup"><span data-stu-id="80875-105">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="80875-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 元素 (格式) ListEntries 元素 (格式) ListEntry 專案 (格式) 之 entryselectedby 專案 (格式) 專案 (格式) ListEntry 專案的 SelectionCondition (格式) 之 entryselectedby for ListEntry 的 SelectionCondition 格式之 entryselectedby 元素</span><span class="sxs-lookup"><span data-stu-id="80875-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="80875-107">語法</span><span class="sxs-lookup"><span data-stu-id="80875-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="80875-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="80875-108">Attributes and Elements</span></span>

<span data-ttu-id="80875-109">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="80875-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="80875-110">屬性</span><span class="sxs-lookup"><span data-stu-id="80875-110">Attributes</span></span>

<span data-ttu-id="80875-111">無。</span><span class="sxs-lookup"><span data-stu-id="80875-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="80875-112">子元素</span><span class="sxs-lookup"><span data-stu-id="80875-112">Child Elements</span></span>

<span data-ttu-id="80875-113">無。</span><span class="sxs-lookup"><span data-stu-id="80875-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="80875-114">父項目</span><span class="sxs-lookup"><span data-stu-id="80875-114">Parent Elements</span></span>

|<span data-ttu-id="80875-115">元素</span><span class="sxs-lookup"><span data-stu-id="80875-115">Element</span></span>|<span data-ttu-id="80875-116">描述</span><span class="sxs-lookup"><span data-stu-id="80875-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80875-117">適用于之 entryselectedby 的 ListEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="80875-117">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="80875-118">定義必須存在才能使用此清單專案的條件。</span><span class="sxs-lookup"><span data-stu-id="80875-118">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="80875-119">文字值</span><span class="sxs-lookup"><span data-stu-id="80875-119">Text Value</span></span>

<span data-ttu-id="80875-120">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="80875-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="80875-121">備註</span><span class="sxs-lookup"><span data-stu-id="80875-121">Remarks</span></span>

<span data-ttu-id="80875-122">選取條件必須指定至少一個要評估的腳本或屬性名稱，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="80875-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="80875-123"> (如需如何使用選取條件的詳細資訊，請參閱 [定義使用視圖專案或專案的條件](./defining-conditions-for-displaying-data.md)。 ) </span><span class="sxs-lookup"><span data-stu-id="80875-123">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="80875-124">如需清單視圖之其他元件的詳細資訊，請參閱 [清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="80875-124">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="80875-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80875-125">See Also</span></span>

[<span data-ttu-id="80875-126">ListEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="80875-126">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="80875-127">ListEntry (格式之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素) </span><span class="sxs-lookup"><span data-stu-id="80875-127">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="80875-128">適用于之 entryselectedby 的 ListEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="80875-128">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="80875-129">清單視圖</span><span class="sxs-lookup"><span data-stu-id="80875-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="80875-130">定義使用視圖專案或專案時的條件</span><span class="sxs-lookup"><span data-stu-id="80875-130">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="80875-131">寫入 Windows PowerShell 格式和類型檔案</span><span class="sxs-lookup"><span data-stu-id="80875-131">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
