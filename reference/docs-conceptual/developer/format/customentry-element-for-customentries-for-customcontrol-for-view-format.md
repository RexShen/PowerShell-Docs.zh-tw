---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之 CustomControl 的 CustomEntries 的 CustomEntry 元素 (格式)
description: 檢視之 CustomControl 的 CustomEntries 的 CustomEntry 元素 (格式)
ms.openlocfilehash: ff481f13e6f16267bdda4c3053faebc96d9a6d3a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646047"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="ab5a4-103">檢視之 CustomControl 的 CustomEntries 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ab5a4-103">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="ab5a4-104">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="ab5a4-104">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="ab5a4-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) CustomControl 元素 (格式) CustomEntries 專案 (格式)  (格式) CustomEntry 專案格式</span><span class="sxs-lookup"><span data-stu-id="ab5a4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ab5a4-106">語法</span><span class="sxs-lookup"><span data-stu-id="ab5a4-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ab5a4-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ab5a4-107">Attributes and Elements</span></span>

<span data-ttu-id="ab5a4-108">下列各節說明屬性、子專案和元素的父元素 `CustomEntry` 。</span><span class="sxs-lookup"><span data-stu-id="ab5a4-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="ab5a4-109">您必須指定定義所顯示的專案。</span><span class="sxs-lookup"><span data-stu-id="ab5a4-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="ab5a4-110">屬性</span><span class="sxs-lookup"><span data-stu-id="ab5a4-110">Attributes</span></span>

<span data-ttu-id="ab5a4-111">無。</span><span class="sxs-lookup"><span data-stu-id="ab5a4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ab5a4-112">子元素</span><span class="sxs-lookup"><span data-stu-id="ab5a4-112">Child Elements</span></span>

|<span data-ttu-id="ab5a4-113">元素</span><span class="sxs-lookup"><span data-stu-id="ab5a4-113">Element</span></span>|<span data-ttu-id="ab5a4-114">描述</span><span class="sxs-lookup"><span data-stu-id="ab5a4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab5a4-115">適用于 CustomEntry 的之 entryselectedby 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="ab5a4-115">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="ab5a4-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="ab5a4-116">Optional element.</span></span><br /><br /> <span data-ttu-id="ab5a4-117">定義 .NET 型別，這些型別會使用自訂控制項視圖的定義或必須存在的條件，才能使用這個定義。</span><span class="sxs-lookup"><span data-stu-id="ab5a4-117">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="ab5a4-118">適用于 CustomEntry 的 CustomItem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="ab5a4-118">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="ab5a4-119">定義自訂控制項定義的控制項。</span><span class="sxs-lookup"><span data-stu-id="ab5a4-119">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ab5a4-120">父項目</span><span class="sxs-lookup"><span data-stu-id="ab5a4-120">Parent Elements</span></span>

|<span data-ttu-id="ab5a4-121">元素</span><span class="sxs-lookup"><span data-stu-id="ab5a4-121">Element</span></span>|<span data-ttu-id="ab5a4-122">描述</span><span class="sxs-lookup"><span data-stu-id="ab5a4-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab5a4-123">檢視之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ab5a4-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="ab5a4-124">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="ab5a4-124">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="ab5a4-125">自訂控制項視圖必須指定一或多個定義。</span><span class="sxs-lookup"><span data-stu-id="ab5a4-125">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ab5a4-126">備註</span><span class="sxs-lookup"><span data-stu-id="ab5a4-126">Remarks</span></span>

<span data-ttu-id="ab5a4-127">在大部分的情況下，每個自訂控制項視圖都只需要一個定義，但如果您想要使用相同的視圖來顯示不同的 .NET 物件，則可以有多個定義。</span><span class="sxs-lookup"><span data-stu-id="ab5a4-127">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="ab5a4-128">在這些情況下，您可以為每個物件或一組物件提供個別的定義。</span><span class="sxs-lookup"><span data-stu-id="ab5a4-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab5a4-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab5a4-129">See Also</span></span>

[<span data-ttu-id="ab5a4-130">檢視的 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ab5a4-130">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="ab5a4-131">適用于 CustomEntry 的 CustomItem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="ab5a4-131">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ab5a4-132">適用于 CustomEntry 的之 entryselectedby 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="ab5a4-132">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ab5a4-133">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="ab5a4-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
