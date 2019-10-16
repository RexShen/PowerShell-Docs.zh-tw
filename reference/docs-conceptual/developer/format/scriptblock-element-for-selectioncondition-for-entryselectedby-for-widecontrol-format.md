---
title: WideControl 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368557"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="f4775-102">WideControl 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="f4775-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="f4775-103">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="f4775-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="f4775-104">當此腳本評估為 `true` 時，就會符合條件，並使用寬專案定義。</span><span class="sxs-lookup"><span data-stu-id="f4775-104">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="f4775-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（格式）之 entryselectedby 元素（代表的 WideEntry （格式） SelectionCondition 元素）之 entryselectedby for WideEntry （Format） ScriptBlock 元素 for 之 entryselectedby for WideEntry 的 SelectionCondition （格式）</span><span class="sxs-lookup"><span data-stu-id="f4775-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f4775-106">語法</span><span class="sxs-lookup"><span data-stu-id="f4775-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f4775-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="f4775-107">Attributes and Elements</span></span>

<span data-ttu-id="f4775-108">下列各節說明屬性、子專案，以及 `ScriptBlock` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="f4775-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f4775-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f4775-109">Attributes</span></span>

<span data-ttu-id="f4775-110">無。</span><span class="sxs-lookup"><span data-stu-id="f4775-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f4775-111">子元素</span><span class="sxs-lookup"><span data-stu-id="f4775-111">Child Elements</span></span>

<span data-ttu-id="f4775-112">無。</span><span class="sxs-lookup"><span data-stu-id="f4775-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f4775-113">父元素</span><span class="sxs-lookup"><span data-stu-id="f4775-113">Parent Elements</span></span>

|<span data-ttu-id="f4775-114">元素</span><span class="sxs-lookup"><span data-stu-id="f4775-114">Element</span></span>|<span data-ttu-id="f4775-115">描述</span><span class="sxs-lookup"><span data-stu-id="f4775-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f4775-116">WideEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f4775-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="f4775-117">定義必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="f4775-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f4775-118">文字值</span><span class="sxs-lookup"><span data-stu-id="f4775-118">Text Value</span></span>

<span data-ttu-id="f4775-119">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="f4775-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="f4775-120">備註</span><span class="sxs-lookup"><span data-stu-id="f4775-120">Remarks</span></span>

<span data-ttu-id="f4775-121">選取條件必須指定至少一個要評估的腳本或屬性名稱，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="f4775-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="f4775-122">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f4775-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f4775-123">如需有關寬視圖之其他元件的詳細資訊，請參閱[Wide view](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="f4775-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f4775-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4775-124">See Also</span></span>

[<span data-ttu-id="f4775-125">建立寬型視圖</span><span class="sxs-lookup"><span data-stu-id="f4775-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="f4775-126">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="f4775-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f4775-127">WideEntry 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f4775-127">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="f4775-128">WideEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f4775-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="f4775-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="f4775-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
