---
title: 針對 WideControl （格式） 的 EntrySelectedBy SelectionCondition TypeName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083802"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="966ba-102">WideControl 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="966ba-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="966ba-103">指定觸發條件的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="966ba-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="966ba-104">有這種類型時，會使用定義。</span><span class="sxs-lookup"><span data-stu-id="966ba-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="966ba-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry 項目 （格式） EntrySelectedBy 項目用於 WideEntry （格式） SelectionCondition 元素EntrySelectedBy WideEntry （格式） 的 EntrySelectedBy 的 SelectionCondition WideEntry （格式） 類型名稱的元素</span><span class="sxs-lookup"><span data-stu-id="966ba-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="966ba-106">語法</span><span class="sxs-lookup"><span data-stu-id="966ba-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="966ba-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="966ba-107">Attributes and Elements</span></span>

<span data-ttu-id="966ba-108">下列各節說明屬性、 子項目和父項目`TypeName`項目。</span><span class="sxs-lookup"><span data-stu-id="966ba-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="966ba-109">屬性</span><span class="sxs-lookup"><span data-stu-id="966ba-109">Attributes</span></span>

<span data-ttu-id="966ba-110">無。</span><span class="sxs-lookup"><span data-stu-id="966ba-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="966ba-111">子元素</span><span class="sxs-lookup"><span data-stu-id="966ba-111">Child Elements</span></span>

<span data-ttu-id="966ba-112">無。</span><span class="sxs-lookup"><span data-stu-id="966ba-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="966ba-113">父項目</span><span class="sxs-lookup"><span data-stu-id="966ba-113">Parent Elements</span></span>

|<span data-ttu-id="966ba-114">項目</span><span class="sxs-lookup"><span data-stu-id="966ba-114">Element</span></span>|<span data-ttu-id="966ba-115">描述</span><span class="sxs-lookup"><span data-stu-id="966ba-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="966ba-116">WideEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="966ba-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="966ba-117">定義要使用此寬項目必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="966ba-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="966ba-118">文字值</span><span class="sxs-lookup"><span data-stu-id="966ba-118">Text Value</span></span>

<span data-ttu-id="966ba-119">指定完整的.NET 型別名稱，例如`System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="966ba-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="966ba-120">備註</span><span class="sxs-lookup"><span data-stu-id="966ba-120">Remarks</span></span>

<span data-ttu-id="966ba-121">選取條件可以指定.NET 型別，或選取範圍設定，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="966ba-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="966ba-122">如需如何使用選擇條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="966ba-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="966ba-123">寬型檢視的其他元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="966ba-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="966ba-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="966ba-124">See Also</span></span>

[<span data-ttu-id="966ba-125">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="966ba-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="966ba-126">定義何時顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="966ba-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="966ba-127">WideEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="966ba-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="966ba-128">針對 WideEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目</span><span class="sxs-lookup"><span data-stu-id="966ba-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="966ba-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="966ba-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
