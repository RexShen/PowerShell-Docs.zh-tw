---
title: SelectionCondition for 之 entryselectedby for EnumerableExpansion (Format 的 ScriptBlock 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 71fd969fd3e5c0a4e39762c9a026982a8ca2a9d1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785365"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="609f1-102">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="609f1-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="609f1-103">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="609f1-103">Specifies the script that triggers the condition.</span></span>

<span data-ttu-id="609f1-104">Configuration 元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 專案 (格式) EnumerableExpansion 專案 (格式) EnumerableExpansion (格式) SelectionCondition 元素，之 entryselectedby 的 EnumerableExpansion (format) ScriptBlock 元素（SelectionCondition for 之 entryselectedby 的 EnumerableExpansion (格式) </span><span class="sxs-lookup"><span data-stu-id="609f1-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="609f1-105">語法</span><span class="sxs-lookup"><span data-stu-id="609f1-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="609f1-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="609f1-106">Attributes and Elements</span></span>

<span data-ttu-id="609f1-107">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="609f1-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="609f1-108">屬性</span><span class="sxs-lookup"><span data-stu-id="609f1-108">Attributes</span></span>

<span data-ttu-id="609f1-109">無。</span><span class="sxs-lookup"><span data-stu-id="609f1-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="609f1-110">子元素</span><span class="sxs-lookup"><span data-stu-id="609f1-110">Child Elements</span></span>

<span data-ttu-id="609f1-111">無。</span><span class="sxs-lookup"><span data-stu-id="609f1-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="609f1-112">父項目</span><span class="sxs-lookup"><span data-stu-id="609f1-112">Parent Elements</span></span>

|<span data-ttu-id="609f1-113">元素</span><span class="sxs-lookup"><span data-stu-id="609f1-113">Element</span></span>|<span data-ttu-id="609f1-114">描述</span><span class="sxs-lookup"><span data-stu-id="609f1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="609f1-115">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="609f1-115">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="609f1-116">定義必須存在的條件，才能展開這個定義的集合物件。</span><span class="sxs-lookup"><span data-stu-id="609f1-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="609f1-117">文字值</span><span class="sxs-lookup"><span data-stu-id="609f1-117">Text Value</span></span>

<span data-ttu-id="609f1-118">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="609f1-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="609f1-119">備註</span><span class="sxs-lookup"><span data-stu-id="609f1-119">Remarks</span></span>

<span data-ttu-id="609f1-120">選取條件必須指定至少一個要評估的腳本或屬性名稱，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="609f1-120">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="609f1-121">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="609f1-121">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="609f1-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="609f1-122">See Also</span></span>

[<span data-ttu-id="609f1-123">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="609f1-123">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="609f1-124">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="609f1-124">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="609f1-125">EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="609f1-125">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="609f1-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="609f1-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
