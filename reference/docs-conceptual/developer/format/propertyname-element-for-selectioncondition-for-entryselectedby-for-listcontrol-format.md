---
title: ListControl 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362287"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="70669-102">ListControl 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="70669-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="70669-103">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="70669-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="70669-104">當這個屬性存在或評估為 `true` 時，就會符合條件，而且會使用清單專案。</span><span class="sxs-lookup"><span data-stu-id="70669-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="70669-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（格式） ListEntries 元素（格式） ListEntry 元素（格式）之 entryselectedby 元素（代表的 ListEntry （格式） SelectionCondition 元素）之 entryselectedby for ListEntry （Format） PropertyName 元素 for 之 entryselectedby for ListEntry 的 SelectionCondition （格式）</span><span class="sxs-lookup"><span data-stu-id="70669-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="70669-106">語法</span><span class="sxs-lookup"><span data-stu-id="70669-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="70669-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="70669-107">Attributes and Elements</span></span>

<span data-ttu-id="70669-108">下列各節說明屬性、子專案，以及 `PropertyName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="70669-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="70669-109">屬性</span><span class="sxs-lookup"><span data-stu-id="70669-109">Attributes</span></span>

<span data-ttu-id="70669-110">無。</span><span class="sxs-lookup"><span data-stu-id="70669-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="70669-111">子元素</span><span class="sxs-lookup"><span data-stu-id="70669-111">Child Elements</span></span>

<span data-ttu-id="70669-112">無。</span><span class="sxs-lookup"><span data-stu-id="70669-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="70669-113">父元素</span><span class="sxs-lookup"><span data-stu-id="70669-113">Parent Elements</span></span>

|<span data-ttu-id="70669-114">元素</span><span class="sxs-lookup"><span data-stu-id="70669-114">Element</span></span>|<span data-ttu-id="70669-115">描述</span><span class="sxs-lookup"><span data-stu-id="70669-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70669-116">ListEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="70669-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="70669-117">定義必須存在才能使用此清單專案的條件。</span><span class="sxs-lookup"><span data-stu-id="70669-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="70669-118">文字值</span><span class="sxs-lookup"><span data-stu-id="70669-118">Text Value</span></span>

<span data-ttu-id="70669-119">指定 .NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="70669-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="70669-120">備註</span><span class="sxs-lookup"><span data-stu-id="70669-120">Remarks</span></span>

<span data-ttu-id="70669-121">選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="70669-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="70669-122">如需如何使用選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="70669-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="70669-123">如需清單視圖之其他元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="70669-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="70669-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70669-124">See Also</span></span>

[<span data-ttu-id="70669-125">建立清單視圖</span><span class="sxs-lookup"><span data-stu-id="70669-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="70669-126">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="70669-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="70669-127">ListEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="70669-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="70669-128">ListEntry 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="70669-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="70669-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="70669-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
