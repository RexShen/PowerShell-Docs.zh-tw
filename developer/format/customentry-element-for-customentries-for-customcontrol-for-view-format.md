---
title: CustomControl 檢視 （格式） 的 CustomEntries CustomEntry 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066442"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="b0e83-102">檢視之 CustomControl 的 CustomEntries 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b0e83-102">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="b0e83-103">提供自訂的控制項檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="b0e83-103">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="b0e83-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目 （格式） CustomEntries 項目 CustomControl CustomEntries 檢視 （格式） 的檢視 （格式） CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="b0e83-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b0e83-105">語法</span><span class="sxs-lookup"><span data-stu-id="b0e83-105">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b0e83-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b0e83-106">Attributes and Elements</span></span>

<span data-ttu-id="b0e83-107">下列各節說明屬性、 子項目和父項目`CustomEntry`項目。</span><span class="sxs-lookup"><span data-stu-id="b0e83-107">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="b0e83-108">您必須指定定義所顯示的項目。</span><span class="sxs-lookup"><span data-stu-id="b0e83-108">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="b0e83-109">屬性</span><span class="sxs-lookup"><span data-stu-id="b0e83-109">Attributes</span></span>

<span data-ttu-id="b0e83-110">無。</span><span class="sxs-lookup"><span data-stu-id="b0e83-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b0e83-111">子元素</span><span class="sxs-lookup"><span data-stu-id="b0e83-111">Child Elements</span></span>

|<span data-ttu-id="b0e83-112">元素</span><span class="sxs-lookup"><span data-stu-id="b0e83-112">Element</span></span>|<span data-ttu-id="b0e83-113">描述</span><span class="sxs-lookup"><span data-stu-id="b0e83-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b0e83-114">EntrySelectedBy CustomEntry 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="b0e83-114">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="b0e83-115">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="b0e83-115">Optional element.</span></span><br /><br /> <span data-ttu-id="b0e83-116">定義使用自訂的控制項檢視或必須存在於要使用此定義條件的定義的.NET 類型。</span><span class="sxs-lookup"><span data-stu-id="b0e83-116">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="b0e83-117">CustomItem CustomEntry 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="b0e83-117">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="b0e83-118">定義自訂控制項定義的控制項。</span><span class="sxs-lookup"><span data-stu-id="b0e83-118">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b0e83-119">父項目</span><span class="sxs-lookup"><span data-stu-id="b0e83-119">Parent Elements</span></span>

|<span data-ttu-id="b0e83-120">項目</span><span class="sxs-lookup"><span data-stu-id="b0e83-120">Element</span></span>|<span data-ttu-id="b0e83-121">描述</span><span class="sxs-lookup"><span data-stu-id="b0e83-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b0e83-122">CustomEntries CustomControl 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="b0e83-122">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="b0e83-123">提供自訂的控制項檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="b0e83-123">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="b0e83-124">自訂控制項的檢視必須指定一個或多個定義。</span><span class="sxs-lookup"><span data-stu-id="b0e83-124">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b0e83-125">備註</span><span class="sxs-lookup"><span data-stu-id="b0e83-125">Remarks</span></span>

<span data-ttu-id="b0e83-126">在大部分情況下，只有一個定義需要為每個自訂的控制項檢視中，但可以有多個定義，如果您想要使用相同的檢視來顯示不同的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="b0e83-126">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="b0e83-127">在這些情況下，您可以針對每個物件或一組物件提供不同的定義。</span><span class="sxs-lookup"><span data-stu-id="b0e83-127">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0e83-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0e83-128">See Also</span></span>

[<span data-ttu-id="b0e83-129">CustomControl 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="b0e83-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="b0e83-130">CustomItem CustomEntry 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="b0e83-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b0e83-131">EntrySelectedBy CustomEntry 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="b0e83-131">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b0e83-132">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="b0e83-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
