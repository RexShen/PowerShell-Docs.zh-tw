---
title: View (Format) 的控制項之 CustomEntry 的之 entryselectedby 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5c82e02d23b1694d05f7a32578ccc5d33686f13f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774247"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="9f5b6-102">檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9f5b6-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="9f5b6-103">定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="9f5b6-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="9f5b6-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="9f5b6-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="9f5b6-105">Configuration 專案 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 CustomControl 格式 CustomEntries 的控制項 (格式) CustomEntry 元素 CustomEntries 的控制項視圖 (格式) 之 entryselectedby 專案（適用于 view (格式的控制項) CustomEntry 專案） (</span><span class="sxs-lookup"><span data-stu-id="9f5b6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9f5b6-106">語法</span><span class="sxs-lookup"><span data-stu-id="9f5b6-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9f5b6-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9f5b6-107">Attributes and Elements</span></span>

<span data-ttu-id="9f5b6-108">下列各節描述元素的屬性、子專案和父項目 `EntrySelectedBy` 。</span><span class="sxs-lookup"><span data-stu-id="9f5b6-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="9f5b6-109">您必須為定義指定至少一個類型、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="9f5b6-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="9f5b6-110">您可以使用的子項目數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="9f5b6-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="9f5b6-111">屬性</span><span class="sxs-lookup"><span data-stu-id="9f5b6-111">Attributes</span></span>

<span data-ttu-id="9f5b6-112">無。</span><span class="sxs-lookup"><span data-stu-id="9f5b6-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9f5b6-113">子元素</span><span class="sxs-lookup"><span data-stu-id="9f5b6-113">Child Elements</span></span>

|<span data-ttu-id="9f5b6-114">元素</span><span class="sxs-lookup"><span data-stu-id="9f5b6-114">Element</span></span>|<span data-ttu-id="9f5b6-115">描述</span><span class="sxs-lookup"><span data-stu-id="9f5b6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9f5b6-116">檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9f5b6-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="9f5b6-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="9f5b6-117">Optional element.</span></span><br /><br /> <span data-ttu-id="9f5b6-118">定義必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="9f5b6-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="9f5b6-119">檢視之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9f5b6-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="9f5b6-120">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="9f5b6-120">Optional element.</span></span><br /><br /> <span data-ttu-id="9f5b6-121">指定一組使用此控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="9f5b6-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="9f5b6-122">檢視之控制項的 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9f5b6-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="9f5b6-123">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="9f5b6-123">Optional element.</span></span><br /><br /> <span data-ttu-id="9f5b6-124">指定使用此控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="9f5b6-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9f5b6-125">父項目</span><span class="sxs-lookup"><span data-stu-id="9f5b6-125">Parent Elements</span></span>

|<span data-ttu-id="9f5b6-126">元素</span><span class="sxs-lookup"><span data-stu-id="9f5b6-126">Element</span></span>|<span data-ttu-id="9f5b6-127">描述</span><span class="sxs-lookup"><span data-stu-id="9f5b6-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9f5b6-128">檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9f5b6-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="9f5b6-129">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="9f5b6-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9f5b6-130">備註</span><span class="sxs-lookup"><span data-stu-id="9f5b6-130">Remarks</span></span>

<span data-ttu-id="9f5b6-131">選取條件是用來定義要使用的定義必須存在的條件，例如當物件具有特定屬性或特定屬性值或腳本評估為時 `true` 。</span><span class="sxs-lookup"><span data-stu-id="9f5b6-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="9f5b6-132">如需選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="9f5b6-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9f5b6-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f5b6-133">See Also</span></span>

[<span data-ttu-id="9f5b6-134">檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9f5b6-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="9f5b6-135">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="9f5b6-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
