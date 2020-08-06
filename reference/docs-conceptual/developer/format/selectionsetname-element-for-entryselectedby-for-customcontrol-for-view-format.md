---
title: CustomControl for View (格式) 的之 entryselectedby 的 SelectionSetName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3728a1886d5406b8fa4888125d1c031d0f9b1b03
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785297"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="ea63b-102">檢視之 CustomControl 的 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ea63b-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="ea63b-103">為清單專案指定一組 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="ea63b-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="ea63b-104">可以為專案指定的選擇集數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="ea63b-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="ea63b-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 專案 (格式) CustomControl for view (CustomEntry 元素的 CustomEntries 專案，CustomEntries for view) format (之 entryselectedby 元素 CustomEntry for SelectionSetName) Format (之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="ea63b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ea63b-106">語法</span><span class="sxs-lookup"><span data-stu-id="ea63b-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ea63b-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ea63b-107">Attributes and Elements</span></span>

<span data-ttu-id="ea63b-108">下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="ea63b-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ea63b-109">屬性</span><span class="sxs-lookup"><span data-stu-id="ea63b-109">Attributes</span></span>

<span data-ttu-id="ea63b-110">無。</span><span class="sxs-lookup"><span data-stu-id="ea63b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ea63b-111">子元素</span><span class="sxs-lookup"><span data-stu-id="ea63b-111">Child Elements</span></span>

<span data-ttu-id="ea63b-112">無。</span><span class="sxs-lookup"><span data-stu-id="ea63b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ea63b-113">父項目</span><span class="sxs-lookup"><span data-stu-id="ea63b-113">Parent Elements</span></span>

|<span data-ttu-id="ea63b-114">元素</span><span class="sxs-lookup"><span data-stu-id="ea63b-114">Element</span></span>|<span data-ttu-id="ea63b-115">描述</span><span class="sxs-lookup"><span data-stu-id="ea63b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ea63b-116">CustomEntry for View (格式的之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="ea63b-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="ea63b-117">定義使用此自訂專案的 .NET 類型，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="ea63b-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ea63b-118">文字值</span><span class="sxs-lookup"><span data-stu-id="ea63b-118">Text Value</span></span>

<span data-ttu-id="ea63b-119">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="ea63b-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="ea63b-120">備註</span><span class="sxs-lookup"><span data-stu-id="ea63b-120">Remarks</span></span>

<span data-ttu-id="ea63b-121">每個自訂控制項專案都必須定義至少一個型別名稱、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="ea63b-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="ea63b-122">當您想要定義多個視圖中使用的一組物件時，通常會使用選取範圍集。</span><span class="sxs-lookup"><span data-stu-id="ea63b-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="ea63b-123">例如，您可能會想要建立一組相同物件的資料表視圖和清單視圖。</span><span class="sxs-lookup"><span data-stu-id="ea63b-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="ea63b-124">如需定義選取集的詳細資訊，請參閱[定義選取範圍集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="ea63b-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="ea63b-125">如需自訂控制項視圖之元件的詳細資訊，請參閱[建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="ea63b-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ea63b-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea63b-126">See Also</span></span>

[<span data-ttu-id="ea63b-127">CustomEntry for View (格式的之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="ea63b-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ea63b-128">自訂控制項視圖</span><span class="sxs-lookup"><span data-stu-id="ea63b-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="ea63b-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="ea63b-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
