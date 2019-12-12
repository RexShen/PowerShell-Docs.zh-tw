---
title: ListControl 之之 entryselectedby 的 SelectionCondition 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361557"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="abb24-102">ListControl 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="abb24-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="abb24-103">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="abb24-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="abb24-104">當此類型存在時，會使用清單專案。</span><span class="sxs-lookup"><span data-stu-id="abb24-104">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="abb24-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（format） ListEntries 元素，用於 ListEntry for ListEntries （Format） ListControl 元素的 ListControl （Format）之 entryselectedby 元素ListEntry for ListControl （format） SelectionCondition 元素，適用于 ListControl for SelectionCondition （格式）之 entryselectedby 的之 entryselectedby for ListControl （Format） TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="abb24-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="abb24-106">語法</span><span class="sxs-lookup"><span data-stu-id="abb24-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="abb24-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="abb24-107">Attributes and Elements</span></span>

<span data-ttu-id="abb24-108">下列各節說明屬性、子專案，以及 `TypeName` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="abb24-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="abb24-109">屬性</span><span class="sxs-lookup"><span data-stu-id="abb24-109">Attributes</span></span>

<span data-ttu-id="abb24-110">無。</span><span class="sxs-lookup"><span data-stu-id="abb24-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="abb24-111">子元素</span><span class="sxs-lookup"><span data-stu-id="abb24-111">Child Elements</span></span>

<span data-ttu-id="abb24-112">無。</span><span class="sxs-lookup"><span data-stu-id="abb24-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="abb24-113">父元素</span><span class="sxs-lookup"><span data-stu-id="abb24-113">Parent Elements</span></span>

|<span data-ttu-id="abb24-114">元素</span><span class="sxs-lookup"><span data-stu-id="abb24-114">Element</span></span>|<span data-ttu-id="abb24-115">描述</span><span class="sxs-lookup"><span data-stu-id="abb24-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="abb24-116">ListControl 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="abb24-116">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="abb24-117">定義必須存在才能使用此清單專案的條件。</span><span class="sxs-lookup"><span data-stu-id="abb24-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="abb24-118">文字值</span><span class="sxs-lookup"><span data-stu-id="abb24-118">Text Value</span></span>

<span data-ttu-id="abb24-119">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="abb24-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="abb24-120">備註</span><span class="sxs-lookup"><span data-stu-id="abb24-120">Remarks</span></span>

<span data-ttu-id="abb24-121">選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="abb24-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="abb24-122">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="abb24-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="abb24-123">如需清單視圖之其他元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="abb24-123">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="abb24-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abb24-124">See Also</span></span>

[<span data-ttu-id="abb24-125">建立清單視圖</span><span class="sxs-lookup"><span data-stu-id="abb24-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="abb24-126">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="abb24-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="abb24-127">ListControl 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="abb24-127">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="abb24-128">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="abb24-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
