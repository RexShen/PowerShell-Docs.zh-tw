---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)
description: 設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)
ms.openlocfilehash: 3967be86a1d6c12c7215ef19d50bac9fafd5ad6d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648283"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="814bc-103">設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="814bc-103">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="814bc-104">提供通用控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="814bc-104">Provides a definition of the common control.</span></span> <span data-ttu-id="814bc-105">當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="814bc-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="814bc-106">設定專案 (格式) 控制項的設定專案 (格式設定的控制項) 控制項專案 (格式) CustomEntries 專案的 CustomControl 設定 (格式) CustomEntry 元素，用於的設定 (格式)  (的控制項 CustomControl 的控制項</span><span class="sxs-lookup"><span data-stu-id="814bc-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="814bc-107">語法</span><span class="sxs-lookup"><span data-stu-id="814bc-107">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="814bc-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="814bc-108">Attributes and Elements</span></span>

<span data-ttu-id="814bc-109">下列各節說明屬性、子專案和元素的父元素 `CustomEntry` 。</span><span class="sxs-lookup"><span data-stu-id="814bc-109">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="814bc-110">您必須指定定義所顯示的專案。</span><span class="sxs-lookup"><span data-stu-id="814bc-110">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="814bc-111">屬性</span><span class="sxs-lookup"><span data-stu-id="814bc-111">Attributes</span></span>

<span data-ttu-id="814bc-112">無。</span><span class="sxs-lookup"><span data-stu-id="814bc-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="814bc-113">子元素</span><span class="sxs-lookup"><span data-stu-id="814bc-113">Child Elements</span></span>

|<span data-ttu-id="814bc-114">元素</span><span class="sxs-lookup"><span data-stu-id="814bc-114">Element</span></span>|<span data-ttu-id="814bc-115">描述</span><span class="sxs-lookup"><span data-stu-id="814bc-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="814bc-116">設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="814bc-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="814bc-117">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="814bc-117">Optional element.</span></span><br /><br /> <span data-ttu-id="814bc-118">定義 .NET 型別，這些型別會使用通用控制項的定義或必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="814bc-118">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="814bc-119">適用于設定之控制項的 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="814bc-119">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="814bc-120">必要元素。</span><span class="sxs-lookup"><span data-stu-id="814bc-120">Required element.</span></span><br /><br /> <span data-ttu-id="814bc-121">定義控制項顯示的資料以及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="814bc-121">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="814bc-122">父項目</span><span class="sxs-lookup"><span data-stu-id="814bc-122">Parent Elements</span></span>

|<span data-ttu-id="814bc-123">元素</span><span class="sxs-lookup"><span data-stu-id="814bc-123">Element</span></span>|<span data-ttu-id="814bc-124">描述</span><span class="sxs-lookup"><span data-stu-id="814bc-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="814bc-125">適用于 CustomControl 的 CustomEntries 元素，適用于 Configuration (格式) </span><span class="sxs-lookup"><span data-stu-id="814bc-125">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="814bc-126">提供通用控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="814bc-126">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="814bc-127">備註</span><span class="sxs-lookup"><span data-stu-id="814bc-127">Remarks</span></span>

<span data-ttu-id="814bc-128">在大部分的情況下，每個通用自訂控制項都只需要一個定義，但如果您想要使用相同的控制項來顯示不同的 .NET 物件，則可以有多個定義。</span><span class="sxs-lookup"><span data-stu-id="814bc-128">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="814bc-129">在這些情況下，您可以為每個物件或一組物件提供個別的定義。</span><span class="sxs-lookup"><span data-stu-id="814bc-129">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="814bc-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="814bc-130">See Also</span></span>

[<span data-ttu-id="814bc-131">適用于 CustomControl 的 CustomEntries 元素，適用于 Configuration (格式) </span><span class="sxs-lookup"><span data-stu-id="814bc-131">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="814bc-132">適用于設定之控制項的 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="814bc-132">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="814bc-133">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="814bc-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
