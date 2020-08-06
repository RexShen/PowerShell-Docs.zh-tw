---
title: SelectionCondition for 之 entryselectedby for WideControl (Format 的 ScriptBlock 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8f2223d4a1217786a930eb82390c24b81d2f72e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787609"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="c24be-102">WideControl 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c24be-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="c24be-103">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="c24be-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="c24be-104">當此腳本評估為時 `true` ，會符合條件，並使用寬專案定義。</span><span class="sxs-lookup"><span data-stu-id="c24be-104">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="c24be-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 元素 (格式) WideEntries 專案 (格式) WideEntry 專案 (格式) 之 entryselectedby 元素（WideEntry 的 SelectionCondition (格式) 之 entryselectedby 元素，WideEntry 適用于 SelectionCondition (格式) </span><span class="sxs-lookup"><span data-stu-id="c24be-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c24be-106">語法</span><span class="sxs-lookup"><span data-stu-id="c24be-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c24be-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c24be-107">Attributes and Elements</span></span>

<span data-ttu-id="c24be-108">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="c24be-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c24be-109">屬性</span><span class="sxs-lookup"><span data-stu-id="c24be-109">Attributes</span></span>

<span data-ttu-id="c24be-110">無。</span><span class="sxs-lookup"><span data-stu-id="c24be-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c24be-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c24be-111">Child Elements</span></span>

<span data-ttu-id="c24be-112">無。</span><span class="sxs-lookup"><span data-stu-id="c24be-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c24be-113">父項目</span><span class="sxs-lookup"><span data-stu-id="c24be-113">Parent Elements</span></span>

|<span data-ttu-id="c24be-114">元素</span><span class="sxs-lookup"><span data-stu-id="c24be-114">Element</span></span>|<span data-ttu-id="c24be-115">描述</span><span class="sxs-lookup"><span data-stu-id="c24be-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c24be-116">WideEntry (格式的之 entryselectedby 的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="c24be-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="c24be-117">定義必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="c24be-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c24be-118">文字值</span><span class="sxs-lookup"><span data-stu-id="c24be-118">Text Value</span></span>

<span data-ttu-id="c24be-119">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="c24be-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="c24be-120">備註</span><span class="sxs-lookup"><span data-stu-id="c24be-120">Remarks</span></span>

<span data-ttu-id="c24be-121">選取條件必須指定至少一個要評估的腳本或屬性名稱，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="c24be-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="c24be-122">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c24be-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="c24be-123">如需有關寬視圖之其他元件的詳細資訊，請參閱[Wide view](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="c24be-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c24be-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c24be-124">See Also</span></span>

[<span data-ttu-id="c24be-125">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="c24be-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="c24be-126">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="c24be-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c24be-127">WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c24be-127">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="c24be-128">WideEntry (格式的之 entryselectedby 的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="c24be-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="c24be-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="c24be-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
