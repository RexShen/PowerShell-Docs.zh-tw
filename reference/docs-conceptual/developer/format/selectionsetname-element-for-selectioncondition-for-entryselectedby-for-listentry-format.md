---
title: ListEntry (格式) 的之 entryselectedby 之 SelectionCondition 的 SelectionSetName 元素Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3666888f149f176126d9a19bdbad62469ca9f064
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787473"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="71235-102">ListEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="71235-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="71235-103">指定觸發條件的 .NET 類型集合。</span><span class="sxs-lookup"><span data-stu-id="71235-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="71235-104">當此集合中的任何類型都存在時，就會符合條件，並使用此清單視圖的定義來顯示該物件。</span><span class="sxs-lookup"><span data-stu-id="71235-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="71235-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListEntries 專案 (格式) ListEntry 專案 (格式) 之 entryselectedby 元素（ListEntry 的 SelectionCondition (format) 之 entryselectedby 元素，ListEntry for SelectionSetName for SelectionCondition (format) </span><span class="sxs-lookup"><span data-stu-id="71235-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="71235-106">語法</span><span class="sxs-lookup"><span data-stu-id="71235-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="71235-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="71235-107">Attributes and Elements</span></span>

<span data-ttu-id="71235-108">下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="71235-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="71235-109">屬性</span><span class="sxs-lookup"><span data-stu-id="71235-109">Attributes</span></span>

<span data-ttu-id="71235-110">無。</span><span class="sxs-lookup"><span data-stu-id="71235-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="71235-111">子元素</span><span class="sxs-lookup"><span data-stu-id="71235-111">Child Elements</span></span>

<span data-ttu-id="71235-112">無。</span><span class="sxs-lookup"><span data-stu-id="71235-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="71235-113">父項目</span><span class="sxs-lookup"><span data-stu-id="71235-113">Parent Elements</span></span>

|<span data-ttu-id="71235-114">元素</span><span class="sxs-lookup"><span data-stu-id="71235-114">Element</span></span>|<span data-ttu-id="71235-115">描述</span><span class="sxs-lookup"><span data-stu-id="71235-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="71235-116">ListEntry (格式的之 entryselectedby 的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="71235-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="71235-117">定義必須存在才能使用此清單視圖定義的條件。</span><span class="sxs-lookup"><span data-stu-id="71235-117">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="71235-118">文字值</span><span class="sxs-lookup"><span data-stu-id="71235-118">Text Value</span></span>

<span data-ttu-id="71235-119">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="71235-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="71235-120">備註</span><span class="sxs-lookup"><span data-stu-id="71235-120">Remarks</span></span>

<span data-ttu-id="71235-121">選取條件可以指定選擇集或 .NET 類型，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="71235-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="71235-122">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="71235-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="71235-123">選取範圍是一組通用的 .NET 物件，可供格式設定檔案定義的任何視圖使用。</span><span class="sxs-lookup"><span data-stu-id="71235-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="71235-124">如需建立和參考選取集的詳細資訊，請參閱[定義物件集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="71235-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="71235-125">如需清單視圖之其他元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="71235-125">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="71235-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71235-126">See Also</span></span>

[<span data-ttu-id="71235-127">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="71235-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="71235-128">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="71235-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="71235-129">ListEntry (格式的之 entryselectedby 的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="71235-129">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="71235-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="71235-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
