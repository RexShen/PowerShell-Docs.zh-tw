---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)
description: 設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)
ms.openlocfilehash: fadcdb69ac71269ba2f2f80baf139bb363d4acba
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666666"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="ac515-103">設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ac515-103">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="ac515-104">定義 .NET 型別，這些型別會使用通用控制項的定義或必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="ac515-104">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="ac515-105">當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="ac515-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="ac515-106">設定專案 (格式) 控制項的設定專案 (格式設定的控制項) 控制項專案 (格式) CustomEntries 專案的 CustomControl 設定 (格式) 的格式 (格式) CustomControl 專案設定 (格式)  (格式的控制項) 格式</span><span class="sxs-lookup"><span data-stu-id="ac515-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ac515-107">語法</span><span class="sxs-lookup"><span data-stu-id="ac515-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ac515-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ac515-108">Attributes and Elements</span></span>

<span data-ttu-id="ac515-109">下列各節說明屬性、子專案和元素的父元素 `EntrySelectedBy` 。</span><span class="sxs-lookup"><span data-stu-id="ac515-109">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ac515-110">屬性</span><span class="sxs-lookup"><span data-stu-id="ac515-110">Attributes</span></span>

<span data-ttu-id="ac515-111">無。</span><span class="sxs-lookup"><span data-stu-id="ac515-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ac515-112">子元素</span><span class="sxs-lookup"><span data-stu-id="ac515-112">Child Elements</span></span>

|<span data-ttu-id="ac515-113">元素</span><span class="sxs-lookup"><span data-stu-id="ac515-113">Element</span></span>|<span data-ttu-id="ac515-114">描述</span><span class="sxs-lookup"><span data-stu-id="ac515-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ac515-115">設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ac515-115">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="ac515-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="ac515-116">Optional element.</span></span><br /><br /> <span data-ttu-id="ac515-117">定義要使用的通用控制項定義必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="ac515-117">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="ac515-118">設定之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ac515-118">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="ac515-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="ac515-119">Optional element.</span></span><br /><br /> <span data-ttu-id="ac515-120">指定一組使用此通用控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="ac515-120">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="ac515-121">設定之控制項的 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ac515-121">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="ac515-122">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="ac515-122">Optional element.</span></span><br /><br /> <span data-ttu-id="ac515-123">指定使用此通用控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="ac515-123">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ac515-124">父項目</span><span class="sxs-lookup"><span data-stu-id="ac515-124">Parent Elements</span></span>

|<span data-ttu-id="ac515-125">元素</span><span class="sxs-lookup"><span data-stu-id="ac515-125">Element</span></span>|<span data-ttu-id="ac515-126">描述</span><span class="sxs-lookup"><span data-stu-id="ac515-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ac515-127">設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ac515-127">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="ac515-128">提供通用控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="ac515-128">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ac515-129">備註</span><span class="sxs-lookup"><span data-stu-id="ac515-129">Remarks</span></span>

<span data-ttu-id="ac515-130">每個定義至少必須指定一個 .NET 類型、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="ac515-130">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="ac515-131">您可以指定的類型、選取集或選取條件數目沒有最大限制。</span><span class="sxs-lookup"><span data-stu-id="ac515-131">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac515-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac515-132">See Also</span></span>

[<span data-ttu-id="ac515-133">設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ac515-133">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="ac515-134">設定之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ac515-134">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="ac515-135">設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ac515-135">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="ac515-136">設定之控制項的 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ac515-136">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="ac515-137">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="ac515-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
