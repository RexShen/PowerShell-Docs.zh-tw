---
title: SelectionCondition for 之 entryselectedby for WideControl (Format 的 TypeName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5021f665b994581f9ff982e13af922d7940ebf2b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783308"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="87776-102">WideControl 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="87776-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="87776-103">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="87776-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="87776-104">當此型別存在時，就會使用定義。</span><span class="sxs-lookup"><span data-stu-id="87776-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="87776-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 專案 (格式) WideEntries 專案 (格式) WideEntry 專案 (格式) 之 entryselectedby 元素（WideEntry 的 SelectionCondition 的之 entryselectedby (格式) WideEntry for SelectionCondition 的之 entryselectedby (格式) </span><span class="sxs-lookup"><span data-stu-id="87776-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="87776-106">語法</span><span class="sxs-lookup"><span data-stu-id="87776-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="87776-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="87776-107">Attributes and Elements</span></span>

<span data-ttu-id="87776-108">下列各節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="87776-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="87776-109">屬性</span><span class="sxs-lookup"><span data-stu-id="87776-109">Attributes</span></span>

<span data-ttu-id="87776-110">無。</span><span class="sxs-lookup"><span data-stu-id="87776-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="87776-111">子元素</span><span class="sxs-lookup"><span data-stu-id="87776-111">Child Elements</span></span>

<span data-ttu-id="87776-112">無。</span><span class="sxs-lookup"><span data-stu-id="87776-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="87776-113">父項目</span><span class="sxs-lookup"><span data-stu-id="87776-113">Parent Elements</span></span>

|<span data-ttu-id="87776-114">元素</span><span class="sxs-lookup"><span data-stu-id="87776-114">Element</span></span>|<span data-ttu-id="87776-115">描述</span><span class="sxs-lookup"><span data-stu-id="87776-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87776-116">WideEntry (格式的之 entryselectedby 的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="87776-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="87776-117">定義必須存在才能使用此寬專案的條件。</span><span class="sxs-lookup"><span data-stu-id="87776-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="87776-118">文字值</span><span class="sxs-lookup"><span data-stu-id="87776-118">Text Value</span></span>

<span data-ttu-id="87776-119">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。</span><span class="sxs-lookup"><span data-stu-id="87776-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="87776-120">備註</span><span class="sxs-lookup"><span data-stu-id="87776-120">Remarks</span></span>

<span data-ttu-id="87776-121">選取條件可以指定 .NET 類型或選擇集，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="87776-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="87776-122">如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="87776-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="87776-123">如需有關寬視圖之其他元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="87776-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="87776-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87776-124">See Also</span></span>

[<span data-ttu-id="87776-125">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="87776-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="87776-126">定義資料顯示時的條件</span><span class="sxs-lookup"><span data-stu-id="87776-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="87776-127">WideEntry (格式的之 entryselectedby 的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="87776-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="87776-128">WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="87776-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="87776-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="87776-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
