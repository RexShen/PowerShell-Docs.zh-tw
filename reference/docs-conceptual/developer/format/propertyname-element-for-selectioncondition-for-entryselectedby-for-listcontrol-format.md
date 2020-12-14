---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)
description: ListControl 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)
ms.openlocfilehash: 1e318e3a29f07b157b9ae7343ba08759db8efbb5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665816"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="42db8-103">ListControl 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="42db8-103">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="42db8-104">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="42db8-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="42db8-105">當這個屬性存在或評估為時，就 `true` 會符合條件，並且會使用清單專案。</span><span class="sxs-lookup"><span data-stu-id="42db8-105">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="42db8-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 元素 (格式) ListEntries 元素 (格式) ListEntry 專案 (格式) 之 entryselectedby 專案 (格式) 專案 (格式) ListEntry 專案的 SelectionCondition (格式) 之 entryselectedby for ListEntry 的 SelectionCondition 格式之 entryselectedby 元素</span><span class="sxs-lookup"><span data-stu-id="42db8-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="42db8-107">語法</span><span class="sxs-lookup"><span data-stu-id="42db8-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="42db8-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="42db8-108">Attributes and Elements</span></span>

<span data-ttu-id="42db8-109">下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="42db8-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="42db8-110">屬性</span><span class="sxs-lookup"><span data-stu-id="42db8-110">Attributes</span></span>

<span data-ttu-id="42db8-111">無。</span><span class="sxs-lookup"><span data-stu-id="42db8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="42db8-112">子元素</span><span class="sxs-lookup"><span data-stu-id="42db8-112">Child Elements</span></span>

<span data-ttu-id="42db8-113">無。</span><span class="sxs-lookup"><span data-stu-id="42db8-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="42db8-114">父項目</span><span class="sxs-lookup"><span data-stu-id="42db8-114">Parent Elements</span></span>

|<span data-ttu-id="42db8-115">元素</span><span class="sxs-lookup"><span data-stu-id="42db8-115">Element</span></span>|<span data-ttu-id="42db8-116">描述</span><span class="sxs-lookup"><span data-stu-id="42db8-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="42db8-117">適用于之 entryselectedby 的 ListEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="42db8-117">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="42db8-118">定義必須存在才能使用此清單專案的條件。</span><span class="sxs-lookup"><span data-stu-id="42db8-118">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="42db8-119">文字值</span><span class="sxs-lookup"><span data-stu-id="42db8-119">Text Value</span></span>

<span data-ttu-id="42db8-120">指定 .NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="42db8-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="42db8-121">備註</span><span class="sxs-lookup"><span data-stu-id="42db8-121">Remarks</span></span>

<span data-ttu-id="42db8-122">選取條件必須至少指定一個屬性名稱或腳本區塊，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="42db8-122">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="42db8-123">如需如何使用選取條件的詳細資訊，請參閱 [定義使用視圖專案或專案的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="42db8-123">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="42db8-124">如需清單視圖之其他元件的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="42db8-124">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="42db8-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42db8-125">See Also</span></span>

[<span data-ttu-id="42db8-126">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="42db8-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="42db8-127">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="42db8-127">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="42db8-128">ListEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="42db8-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="42db8-129">適用于 ListEntry (格式之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="42db8-129">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="42db8-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="42db8-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
