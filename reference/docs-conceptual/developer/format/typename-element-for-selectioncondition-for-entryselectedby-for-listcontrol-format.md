---
title: SelectionCondition for 之 entryselectedby for ListControl (Format 的 TypeName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: bc58d630e65b316f9223bf3c529f928358e38ebc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787370"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="1df70-102">ListControl 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1df70-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="1df70-103">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="1df70-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="1df70-104">當此類型存在時，會使用清單專案。</span><span class="sxs-lookup"><span data-stu-id="1df70-104">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="1df70-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListControl (格式) ListEntry 元素（ListEntries for ListControl (format) 之 entryselectedby 元素 (ListEntry for ListControl 的 SelectionCondition) 格式 (之 entryselectedby 元素 ListControl 的 SelectionCondition 專案</span><span class="sxs-lookup"><span data-stu-id="1df70-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1df70-106">語法</span><span class="sxs-lookup"><span data-stu-id="1df70-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1df70-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1df70-107">Attributes and Elements</span></span>

<span data-ttu-id="1df70-108">下列各節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="1df70-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1df70-109">屬性</span><span class="sxs-lookup"><span data-stu-id="1df70-109">Attributes</span></span>

<span data-ttu-id="1df70-110">無。</span><span class="sxs-lookup"><span data-stu-id="1df70-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1df70-111">子元素</span><span class="sxs-lookup"><span data-stu-id="1df70-111">Child Elements</span></span>

<span data-ttu-id="1df70-112">無。</span><span class="sxs-lookup"><span data-stu-id="1df70-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1df70-113">父項目</span><span class="sxs-lookup"><span data-stu-id="1df70-113">Parent Elements</span></span>

|<span data-ttu-id="1df70-114">元素</span><span class="sxs-lookup"><span data-stu-id="1df70-114">Element</span></span>|<span data-ttu-id="1df70-115">描述</span><span class="sxs-lookup"><span data-stu-id="1df70-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1df70-116">ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1df70-116">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="1df70-117">定義必須存在才能使用此清單專案的條件。</span><span class="sxs-lookup"><span data-stu-id="1df70-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1df70-118">文字值</span><span class="sxs-lookup"><span data-stu-id="1df70-118">Text Value</span></span>

<span data-ttu-id="1df70-119">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。</span><span class="sxs-lookup"><span data-stu-id="1df70-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="1df70-120">備註</span><span class="sxs-lookup"><span data-stu-id="1df70-120">Remarks</span></span>

<span data-ttu-id="1df70-121">選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="1df70-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="1df70-122">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="1df70-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1df70-123">如需清單視圖之其他元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="1df70-123">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1df70-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1df70-124">See Also</span></span>

[<span data-ttu-id="1df70-125">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="1df70-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="1df70-126">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="1df70-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1df70-127">ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1df70-127">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="1df70-128">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="1df70-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
