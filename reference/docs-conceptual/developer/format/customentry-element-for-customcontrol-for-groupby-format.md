---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之 CustomControl 的 CustomEntry 元素 (格式)
description: GroupBy 之 CustomControl 的 CustomEntry 元素 (格式)
ms.openlocfilehash: 0df2ff9c15308939e6d2552f51e2961bdabc59fb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646072"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="3ca42-103">GroupBy 之 CustomControl 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3ca42-103">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="3ca42-104">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="3ca42-104">Provides a definition of the control.</span></span> <span data-ttu-id="3ca42-105">定義如何顯示新的物件群組時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="3ca42-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="3ca42-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy (格式) CustomEntries 元素適用于 groupby (格式) CustomEntry 專案用於 CustomControl 的 GroupBy (格式) </span><span class="sxs-lookup"><span data-stu-id="3ca42-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3ca42-107">語法</span><span class="sxs-lookup"><span data-stu-id="3ca42-107">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3ca42-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3ca42-108">Attributes and Elements</span></span>

<span data-ttu-id="3ca42-109">下列各節說明屬性、子專案和元素的父元素 `CustomEntry` 。</span><span class="sxs-lookup"><span data-stu-id="3ca42-109">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3ca42-110">屬性</span><span class="sxs-lookup"><span data-stu-id="3ca42-110">Attributes</span></span>

<span data-ttu-id="3ca42-111">無。</span><span class="sxs-lookup"><span data-stu-id="3ca42-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3ca42-112">子元素</span><span class="sxs-lookup"><span data-stu-id="3ca42-112">Child Elements</span></span>

|<span data-ttu-id="3ca42-113">元素</span><span class="sxs-lookup"><span data-stu-id="3ca42-113">Element</span></span>|<span data-ttu-id="3ca42-114">描述</span><span class="sxs-lookup"><span data-stu-id="3ca42-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ca42-115">GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3ca42-115">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="3ca42-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="3ca42-116">Optional element.</span></span><br /><br /> <span data-ttu-id="3ca42-117">定義使用此控制項定義的 .NET 型別，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="3ca42-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="3ca42-118">GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3ca42-118">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="3ca42-119">必要元素。</span><span class="sxs-lookup"><span data-stu-id="3ca42-119">Required element.</span></span><br /><br /> <span data-ttu-id="3ca42-120">定義控制項顯示資料的方式。</span><span class="sxs-lookup"><span data-stu-id="3ca42-120">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3ca42-121">父項目</span><span class="sxs-lookup"><span data-stu-id="3ca42-121">Parent Elements</span></span>

|<span data-ttu-id="3ca42-122">元素</span><span class="sxs-lookup"><span data-stu-id="3ca42-122">Element</span></span>|<span data-ttu-id="3ca42-123">描述</span><span class="sxs-lookup"><span data-stu-id="3ca42-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ca42-124">GroupBy 之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3ca42-124">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="3ca42-125">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="3ca42-125">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3ca42-126">備註</span><span class="sxs-lookup"><span data-stu-id="3ca42-126">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="3ca42-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ca42-127">See Also</span></span>

[<span data-ttu-id="3ca42-128">GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3ca42-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="3ca42-129">GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3ca42-129">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="3ca42-130">GroupBy 之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3ca42-130">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="3ca42-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="3ca42-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
