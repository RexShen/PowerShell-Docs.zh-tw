---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)
description: 檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)
ms.openlocfilehash: 29b0574a95d81962fb3f72a526f89273baeea647
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660255"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="09251-103">檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="09251-103">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="09251-104">定義使用此控制項定義的 .NET 型別，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="09251-104">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="09251-105">當定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="09251-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="09251-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) Control 元素 (format) format (format 控制項控制項的控制項) CustomEntries (格式控制項的控制項) 專案 (格式) 專案 (格式) 專案 (格式) 專案格式控制項的</span><span class="sxs-lookup"><span data-stu-id="09251-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="09251-107">語法</span><span class="sxs-lookup"><span data-stu-id="09251-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="09251-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="09251-108">Attributes and Elements</span></span>

<span data-ttu-id="09251-109">下列各節描述專案的屬性、子項目和父元素 `EntrySelectedBy` 。</span><span class="sxs-lookup"><span data-stu-id="09251-109">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="09251-110">您必須為定義指定至少一個類型、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="09251-110">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="09251-111">您可以使用的子項目數目沒有最大限制。</span><span class="sxs-lookup"><span data-stu-id="09251-111">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="09251-112">屬性</span><span class="sxs-lookup"><span data-stu-id="09251-112">Attributes</span></span>

<span data-ttu-id="09251-113">無。</span><span class="sxs-lookup"><span data-stu-id="09251-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="09251-114">子元素</span><span class="sxs-lookup"><span data-stu-id="09251-114">Child Elements</span></span>

|<span data-ttu-id="09251-115">元素</span><span class="sxs-lookup"><span data-stu-id="09251-115">Element</span></span>|<span data-ttu-id="09251-116">描述</span><span class="sxs-lookup"><span data-stu-id="09251-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="09251-117">檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="09251-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="09251-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="09251-118">Optional element.</span></span><br /><br /> <span data-ttu-id="09251-119">定義必須存在的條件，才能使用這個定義。</span><span class="sxs-lookup"><span data-stu-id="09251-119">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="09251-120">檢視之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="09251-120">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="09251-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="09251-121">Optional element.</span></span><br /><br /> <span data-ttu-id="09251-122">指定一組使用此控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="09251-122">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="09251-123">檢視之控制項的 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="09251-123">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="09251-124">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="09251-124">Optional element.</span></span><br /><br /> <span data-ttu-id="09251-125">指定使用此控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="09251-125">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="09251-126">父項目</span><span class="sxs-lookup"><span data-stu-id="09251-126">Parent Elements</span></span>

|<span data-ttu-id="09251-127">元素</span><span class="sxs-lookup"><span data-stu-id="09251-127">Element</span></span>|<span data-ttu-id="09251-128">描述</span><span class="sxs-lookup"><span data-stu-id="09251-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="09251-129">檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="09251-129">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="09251-130">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="09251-130">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="09251-131">備註</span><span class="sxs-lookup"><span data-stu-id="09251-131">Remarks</span></span>

<span data-ttu-id="09251-132">選取條件是用來定義必須存在才能使用定義的條件，例如當物件有特定屬性，或當特定屬性值或腳本評估為時 `true` 。</span><span class="sxs-lookup"><span data-stu-id="09251-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="09251-133">如需選取條件的詳細資訊，請參閱 [定義使用視圖專案或專案的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="09251-133">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="09251-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09251-134">See Also</span></span>

[<span data-ttu-id="09251-135">檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="09251-135">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="09251-136">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="09251-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
