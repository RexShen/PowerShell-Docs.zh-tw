---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)
description: WideControl 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)
ms.openlocfilehash: 53d3eba9d453dbcc96afbe8f81a16b61573f2874
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651969"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="113e4-103">WideControl 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="113e4-103">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="113e4-104">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="113e4-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="113e4-105">當此腳本評估為時 `true` ，就會符合條件，並且會使用寬專案定義。</span><span class="sxs-lookup"><span data-stu-id="113e4-105">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="113e4-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 元素 (格式) WideEntries 元素 (格式) WideEntry 專案 (格式) 之 entryselectedby 專案 (格式) 專案 (格式) WideEntry 專案的 SelectionCondition (格式) 之 entryselectedby for WideEntry 的 SelectionCondition 格式之 entryselectedby 元素</span><span class="sxs-lookup"><span data-stu-id="113e4-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="113e4-107">語法</span><span class="sxs-lookup"><span data-stu-id="113e4-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="113e4-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="113e4-108">Attributes and Elements</span></span>

<span data-ttu-id="113e4-109">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="113e4-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="113e4-110">屬性</span><span class="sxs-lookup"><span data-stu-id="113e4-110">Attributes</span></span>

<span data-ttu-id="113e4-111">無。</span><span class="sxs-lookup"><span data-stu-id="113e4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="113e4-112">子元素</span><span class="sxs-lookup"><span data-stu-id="113e4-112">Child Elements</span></span>

<span data-ttu-id="113e4-113">無。</span><span class="sxs-lookup"><span data-stu-id="113e4-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="113e4-114">父項目</span><span class="sxs-lookup"><span data-stu-id="113e4-114">Parent Elements</span></span>

|<span data-ttu-id="113e4-115">元素</span><span class="sxs-lookup"><span data-stu-id="113e4-115">Element</span></span>|<span data-ttu-id="113e4-116">描述</span><span class="sxs-lookup"><span data-stu-id="113e4-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="113e4-117">適用于之 entryselectedby 的 WideEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="113e4-117">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="113e4-118">定義必須存在的條件，才能使用這個定義。</span><span class="sxs-lookup"><span data-stu-id="113e4-118">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="113e4-119">文字值</span><span class="sxs-lookup"><span data-stu-id="113e4-119">Text Value</span></span>

<span data-ttu-id="113e4-120">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="113e4-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="113e4-121">備註</span><span class="sxs-lookup"><span data-stu-id="113e4-121">Remarks</span></span>

<span data-ttu-id="113e4-122">選取條件必須指定至少一個要評估的腳本或屬性名稱，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="113e4-122">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="113e4-123">如需如何使用選取條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="113e4-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="113e4-124">如需廣泛視圖的其他元件的詳細資訊，請參閱 [Wide view](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="113e4-124">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="113e4-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="113e4-125">See Also</span></span>

[<span data-ttu-id="113e4-126">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="113e4-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="113e4-127">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="113e4-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="113e4-128">WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="113e4-128">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="113e4-129">適用于之 entryselectedby 的 WideEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="113e4-129">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="113e4-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="113e4-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
