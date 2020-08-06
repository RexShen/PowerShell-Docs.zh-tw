---
title: SelectionCondition for 之 entryselectedby for ListControl (Format 的 ScriptBlock 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 56bd04c9af74bdaa7a186a208fc15a67cb08b004
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772853"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="c3f75-102">ListControl 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c3f75-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="c3f75-103">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="c3f75-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="c3f75-104">當此腳本評估為時 `true` ，會符合條件，而且會使用清單專案。</span><span class="sxs-lookup"><span data-stu-id="c3f75-104">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="c3f75-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 元素 (格式) ListEntries 專案 (格式) ListEntry 專案 (格式) 之 entryselectedby 元素（ListEntry 的 SelectionCondition (格式) 之 entryselectedby 元素，ListEntry 適用于 SelectionCondition (格式) </span><span class="sxs-lookup"><span data-stu-id="c3f75-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c3f75-106">語法</span><span class="sxs-lookup"><span data-stu-id="c3f75-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c3f75-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c3f75-107">Attributes and Elements</span></span>

<span data-ttu-id="c3f75-108">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="c3f75-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c3f75-109">屬性</span><span class="sxs-lookup"><span data-stu-id="c3f75-109">Attributes</span></span>

<span data-ttu-id="c3f75-110">無。</span><span class="sxs-lookup"><span data-stu-id="c3f75-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c3f75-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c3f75-111">Child Elements</span></span>

<span data-ttu-id="c3f75-112">無。</span><span class="sxs-lookup"><span data-stu-id="c3f75-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c3f75-113">父項目</span><span class="sxs-lookup"><span data-stu-id="c3f75-113">Parent Elements</span></span>

|<span data-ttu-id="c3f75-114">元素</span><span class="sxs-lookup"><span data-stu-id="c3f75-114">Element</span></span>|<span data-ttu-id="c3f75-115">描述</span><span class="sxs-lookup"><span data-stu-id="c3f75-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c3f75-116">ListEntry (格式的之 entryselectedby 的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="c3f75-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="c3f75-117">定義必須存在才能使用此清單專案的條件。</span><span class="sxs-lookup"><span data-stu-id="c3f75-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c3f75-118">文字值</span><span class="sxs-lookup"><span data-stu-id="c3f75-118">Text Value</span></span>

<span data-ttu-id="c3f75-119">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="c3f75-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3f75-120">備註</span><span class="sxs-lookup"><span data-stu-id="c3f75-120">Remarks</span></span>

<span data-ttu-id="c3f75-121">選取條件必須指定至少一個要評估的腳本或屬性名稱，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="c3f75-121">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="c3f75-122"> (需如何使用選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)。 ) </span><span class="sxs-lookup"><span data-stu-id="c3f75-122">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="c3f75-123">如需清單視圖之其他元件的詳細資訊，請參閱[清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="c3f75-123">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c3f75-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3f75-124">See Also</span></span>

[<span data-ttu-id="c3f75-125">ListEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="c3f75-125">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="c3f75-126">SelectionCondition for 之 entryselectedby for ListEntry (Format 的 PropertyName 元素) </span><span class="sxs-lookup"><span data-stu-id="c3f75-126">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="c3f75-127">ListEntry (格式的之 entryselectedby 的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="c3f75-127">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="c3f75-128">清單視圖</span><span class="sxs-lookup"><span data-stu-id="c3f75-128">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c3f75-129">定義使用視圖專案或專案時的條件</span><span class="sxs-lookup"><span data-stu-id="c3f75-129">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c3f75-130">撰寫 Windows PowerShell 格式化和類型檔案</span><span class="sxs-lookup"><span data-stu-id="c3f75-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
