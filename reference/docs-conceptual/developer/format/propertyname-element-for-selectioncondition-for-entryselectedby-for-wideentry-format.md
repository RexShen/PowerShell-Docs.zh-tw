---
ms.date: 09/13/2016
ms.topic: reference
title: WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)
description: WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)
ms.openlocfilehash: bda34b0c1e97fb85536132bedcec3986072801b7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665697"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="7e6b4-103">WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7e6b4-103">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="7e6b4-104">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="7e6b4-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="7e6b4-105">當這個屬性存在或評估為時， `true` 就會符合條件，並使用定義。</span><span class="sxs-lookup"><span data-stu-id="7e6b4-105">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="7e6b4-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 元素 (格式) WideEntries 元素 (格式) WideEntry 專案 (格式) 之 entryselectedby 專案 (格式) 專案 (格式) WideEntry 專案的 SelectionCondition (格式) 之 entryselectedby for WideEntry 的 SelectionCondition 格式之 entryselectedby 元素</span><span class="sxs-lookup"><span data-stu-id="7e6b4-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7e6b4-107">語法</span><span class="sxs-lookup"><span data-stu-id="7e6b4-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="7e6b4-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7e6b4-108">Attributes and Elements</span></span>

<span data-ttu-id="7e6b4-109">下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="7e6b4-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7e6b4-110">屬性</span><span class="sxs-lookup"><span data-stu-id="7e6b4-110">Attributes</span></span>

<span data-ttu-id="7e6b4-111">無。</span><span class="sxs-lookup"><span data-stu-id="7e6b4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7e6b4-112">子元素</span><span class="sxs-lookup"><span data-stu-id="7e6b4-112">Child Elements</span></span>

<span data-ttu-id="7e6b4-113">無。</span><span class="sxs-lookup"><span data-stu-id="7e6b4-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7e6b4-114">父項目</span><span class="sxs-lookup"><span data-stu-id="7e6b4-114">Parent Elements</span></span>

|<span data-ttu-id="7e6b4-115">元素</span><span class="sxs-lookup"><span data-stu-id="7e6b4-115">Element</span></span>|<span data-ttu-id="7e6b4-116">描述</span><span class="sxs-lookup"><span data-stu-id="7e6b4-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7e6b4-117">適用于之 entryselectedby 的 WideEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="7e6b4-117">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="7e6b4-118">定義必須存在的條件，才能使用這個定義。</span><span class="sxs-lookup"><span data-stu-id="7e6b4-118">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7e6b4-119">文字值</span><span class="sxs-lookup"><span data-stu-id="7e6b4-119">Text Value</span></span>

<span data-ttu-id="7e6b4-120">指定 .NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="7e6b4-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="7e6b4-121">備註</span><span class="sxs-lookup"><span data-stu-id="7e6b4-121">Remarks</span></span>

<span data-ttu-id="7e6b4-122">選取條件必須指定至少一個屬性名稱或要評估的腳本，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="7e6b4-122">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="7e6b4-123">如需如何使用選取條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7e6b4-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="7e6b4-124">如需廣泛視圖的其他元件的詳細資訊，請參閱 [Wide view](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="7e6b4-124">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7e6b4-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e6b4-125">See Also</span></span>

[<span data-ttu-id="7e6b4-126">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="7e6b4-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="7e6b4-127">定義顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="7e6b4-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7e6b4-128">適用于 WideEntry (格式之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="7e6b4-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="7e6b4-129">適用于之 entryselectedby 的 WideEntry (格式的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="7e6b4-129">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="7e6b4-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="7e6b4-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
