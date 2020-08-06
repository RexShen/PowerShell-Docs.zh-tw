---
title: 適用于之 entryselectedby 之 GroupBy (格式的 SelectionSetName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 362f7844c09a52494387a62e329adfb309767427
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785280"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="0ec63-102">GroupBy 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0ec63-102">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="0ec63-103">為清單專案指定一組 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="0ec63-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="0ec63-104">可以為專案指定的選擇集數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="0ec63-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="0ec63-105">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="0ec63-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="0ec63-106">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素（GroupBy (格式）) CustomEntries 專案（適用于 CustomEntry 的 groupby (格式) CustomControl 專案 (之 entryselectedby 元素（適用于 groupby) 格式的 CustomEntry） (SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="0ec63-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0ec63-107">語法</span><span class="sxs-lookup"><span data-stu-id="0ec63-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0ec63-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0ec63-108">Attributes and Elements</span></span>

<span data-ttu-id="0ec63-109">下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。</span><span class="sxs-lookup"><span data-stu-id="0ec63-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0ec63-110">屬性</span><span class="sxs-lookup"><span data-stu-id="0ec63-110">Attributes</span></span>

<span data-ttu-id="0ec63-111">無。</span><span class="sxs-lookup"><span data-stu-id="0ec63-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0ec63-112">子元素</span><span class="sxs-lookup"><span data-stu-id="0ec63-112">Child Elements</span></span>

<span data-ttu-id="0ec63-113">無。</span><span class="sxs-lookup"><span data-stu-id="0ec63-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0ec63-114">父項目</span><span class="sxs-lookup"><span data-stu-id="0ec63-114">Parent Elements</span></span>

|<span data-ttu-id="0ec63-115">元素</span><span class="sxs-lookup"><span data-stu-id="0ec63-115">Element</span></span>|<span data-ttu-id="0ec63-116">描述</span><span class="sxs-lookup"><span data-stu-id="0ec63-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0ec63-117">GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0ec63-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="0ec63-118">定義使用此自訂專案的 .NET 類型，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="0ec63-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0ec63-119">文字值</span><span class="sxs-lookup"><span data-stu-id="0ec63-119">Text Value</span></span>

<span data-ttu-id="0ec63-120">指定選取範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="0ec63-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="0ec63-121">備註</span><span class="sxs-lookup"><span data-stu-id="0ec63-121">Remarks</span></span>

<span data-ttu-id="0ec63-122">每個自訂控制項定義都必須定義至少一個型別名稱、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="0ec63-122">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="0ec63-123">當您想要定義多個視圖中使用的一組物件時，通常會使用選取範圍集。</span><span class="sxs-lookup"><span data-stu-id="0ec63-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="0ec63-124">例如，您可能會想要建立一組相同物件的資料表視圖和清單視圖。</span><span class="sxs-lookup"><span data-stu-id="0ec63-124">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="0ec63-125">如需定義選取集的詳細資訊，請參閱[定義選取範圍集合](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="0ec63-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="0ec63-126">如需自訂控制項視圖之元件的詳細資訊，請參閱[建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="0ec63-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0ec63-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ec63-127">See Also</span></span>

[<span data-ttu-id="0ec63-128">GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0ec63-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="0ec63-129">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="0ec63-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="0ec63-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="0ec63-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
