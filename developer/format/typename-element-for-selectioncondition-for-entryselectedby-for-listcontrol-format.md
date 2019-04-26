---
title: 針對 ListControl （格式） 的 EntrySelectedBy SelectionCondition TypeName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083853"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="2af09-102">ListControl 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2af09-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="2af09-103">指定觸發條件的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="2af09-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="2af09-104">當有此類型，則會使用清單項目。</span><span class="sxs-lookup"><span data-stu-id="2af09-104">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="2af09-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目用於 ListControl （格式） EntrySelectedBy 元素 ListEntries ListControl （格式） ListEntry 項目ListEntry ListControl （格式） 的 EntrySelectedBy 的 SelectionCondition ListControl （格式） TypeName 元素 EntrySelectedBy ListControl （格式） SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="2af09-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2af09-106">語法</span><span class="sxs-lookup"><span data-stu-id="2af09-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2af09-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2af09-107">Attributes and Elements</span></span>

<span data-ttu-id="2af09-108">下列各節說明屬性、 子項目和父項目`TypeName`項目。</span><span class="sxs-lookup"><span data-stu-id="2af09-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2af09-109">屬性</span><span class="sxs-lookup"><span data-stu-id="2af09-109">Attributes</span></span>

<span data-ttu-id="2af09-110">無。</span><span class="sxs-lookup"><span data-stu-id="2af09-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2af09-111">子元素</span><span class="sxs-lookup"><span data-stu-id="2af09-111">Child Elements</span></span>

<span data-ttu-id="2af09-112">無。</span><span class="sxs-lookup"><span data-stu-id="2af09-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2af09-113">父項目</span><span class="sxs-lookup"><span data-stu-id="2af09-113">Parent Elements</span></span>

|<span data-ttu-id="2af09-114">項目</span><span class="sxs-lookup"><span data-stu-id="2af09-114">Element</span></span>|<span data-ttu-id="2af09-115">描述</span><span class="sxs-lookup"><span data-stu-id="2af09-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2af09-116">ListControl （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="2af09-116">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="2af09-117">定義要使用此清單項目必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="2af09-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2af09-118">文字值</span><span class="sxs-lookup"><span data-stu-id="2af09-118">Text Value</span></span>

<span data-ttu-id="2af09-119">指定完整的.NET 型別名稱，例如`System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="2af09-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="2af09-120">備註</span><span class="sxs-lookup"><span data-stu-id="2af09-120">Remarks</span></span>

<span data-ttu-id="2af09-121">選取條件可以指定任意數目的.NET 型別，或選取項目集，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="2af09-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="2af09-122">如需如何使用選擇條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="2af09-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="2af09-123">如需其他詳細資訊的元件清單檢視中，請參閱[建立清單檢視](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="2af09-123">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2af09-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2af09-124">See Also</span></span>

[<span data-ttu-id="2af09-125">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="2af09-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="2af09-126">定義何時顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="2af09-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2af09-127">ListControl （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="2af09-127">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="2af09-128">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="2af09-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
