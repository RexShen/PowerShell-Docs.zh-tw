---
title: WideEntry (格式的之 entryselectedby 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ba0a776839c39d753d12859335388c5326639fd4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774077"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="7f7a6-102">WideEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7f7a6-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="7f7a6-103">定義使用此寬視圖定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="7f7a6-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="7f7a6-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 元素 (格式) WideEntries 專案 (格式) WideEntry 專案 (格式) 之 entryselectedby 元素用於 WideEntry (格式) </span><span class="sxs-lookup"><span data-stu-id="7f7a6-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7f7a6-105">語法</span><span class="sxs-lookup"><span data-stu-id="7f7a6-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7f7a6-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7f7a6-106">Attributes and Elements</span></span>

<span data-ttu-id="7f7a6-107">下列各節說明屬性、子專案和元素的父元素 `EntrySelectedBy` 。</span><span class="sxs-lookup"><span data-stu-id="7f7a6-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7f7a6-108">屬性</span><span class="sxs-lookup"><span data-stu-id="7f7a6-108">Attributes</span></span>

<span data-ttu-id="7f7a6-109">無。</span><span class="sxs-lookup"><span data-stu-id="7f7a6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7f7a6-110">子元素</span><span class="sxs-lookup"><span data-stu-id="7f7a6-110">Child Elements</span></span>

|<span data-ttu-id="7f7a6-111">元素</span><span class="sxs-lookup"><span data-stu-id="7f7a6-111">Element</span></span>|<span data-ttu-id="7f7a6-112">描述</span><span class="sxs-lookup"><span data-stu-id="7f7a6-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7f7a6-113">WideEntry (格式的之 entryselectedby 的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="7f7a6-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="7f7a6-114">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="7f7a6-114">Optional element.</span></span><br /><br /> <span data-ttu-id="7f7a6-115">定義必須存在的條件，才能使用此寬視圖定義。</span><span class="sxs-lookup"><span data-stu-id="7f7a6-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="7f7a6-116">WideEntry (格式的之 entryselectedby 的 SelectionSetName 元素) </span><span class="sxs-lookup"><span data-stu-id="7f7a6-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="7f7a6-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="7f7a6-117">Optional element.</span></span><br /><br /> <span data-ttu-id="7f7a6-118">指定一組使用此寬視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="7f7a6-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="7f7a6-119">WideEntry 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7f7a6-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="7f7a6-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="7f7a6-120">Optional element.</span></span><br /><br /> <span data-ttu-id="7f7a6-121">指定使用此寬視圖定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="7f7a6-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7f7a6-122">父項目</span><span class="sxs-lookup"><span data-stu-id="7f7a6-122">Parent Elements</span></span>

|<span data-ttu-id="7f7a6-123">元素</span><span class="sxs-lookup"><span data-stu-id="7f7a6-123">Element</span></span>|<span data-ttu-id="7f7a6-124">描述</span><span class="sxs-lookup"><span data-stu-id="7f7a6-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7f7a6-125">WideEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="7f7a6-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="7f7a6-126">提供寬視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="7f7a6-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7f7a6-127">備註</span><span class="sxs-lookup"><span data-stu-id="7f7a6-127">Remarks</span></span>

<span data-ttu-id="7f7a6-128">您必須為寬視圖定義指定至少一個類型、選取範圍或選取條件。</span><span class="sxs-lookup"><span data-stu-id="7f7a6-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="7f7a6-129">您可以使用的子項目數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="7f7a6-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="7f7a6-130">選取條件是用來定義要使用的定義必須存在的條件，例如，當物件具有特定屬性或特定屬性值或腳本值評估為時 `true` 。</span><span class="sxs-lookup"><span data-stu-id="7f7a6-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="7f7a6-131">如需選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7f7a6-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="7f7a6-132">如需有關寬視圖之其他元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="7f7a6-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7f7a6-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f7a6-133">See Also</span></span>

[<span data-ttu-id="7f7a6-134">WideEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="7f7a6-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="7f7a6-135">WideEntry (格式的之 entryselectedby 的 SelectionCondition 元素) </span><span class="sxs-lookup"><span data-stu-id="7f7a6-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="7f7a6-136">WideEntry (格式的之 entryselectedby 的 SelectionSetName 元素) </span><span class="sxs-lookup"><span data-stu-id="7f7a6-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="7f7a6-137">WideEntry 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7f7a6-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="7f7a6-138">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="7f7a6-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="7f7a6-139">定義用於顯示資料的條件</span><span class="sxs-lookup"><span data-stu-id="7f7a6-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7f7a6-140">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="7f7a6-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
