---
title: CustomControl for View 的 CustomEntries 的 CustomEntry 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364017"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="88367-102">檢視之 CustomControl 的 CustomEntries 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="88367-102">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="88367-103">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="88367-103">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="88367-104">CustomEntry for view 的 CustomControl for View （Format） CustomEntries 元素的設定元素（格式） ViewDefinitions 元素（格式） CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="88367-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="88367-105">語法</span><span class="sxs-lookup"><span data-stu-id="88367-105">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="88367-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="88367-106">Attributes and Elements</span></span>

<span data-ttu-id="88367-107">下列各節說明屬性、子專案，以及 `CustomEntry` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="88367-107">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="88367-108">您必須指定定義所顯示的專案。</span><span class="sxs-lookup"><span data-stu-id="88367-108">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="88367-109">屬性</span><span class="sxs-lookup"><span data-stu-id="88367-109">Attributes</span></span>

<span data-ttu-id="88367-110">無。</span><span class="sxs-lookup"><span data-stu-id="88367-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="88367-111">子元素</span><span class="sxs-lookup"><span data-stu-id="88367-111">Child Elements</span></span>

|<span data-ttu-id="88367-112">元素</span><span class="sxs-lookup"><span data-stu-id="88367-112">Element</span></span>|<span data-ttu-id="88367-113">描述</span><span class="sxs-lookup"><span data-stu-id="88367-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="88367-114">CustomEntry for View 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="88367-114">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="88367-115">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="88367-115">Optional element.</span></span><br /><br /> <span data-ttu-id="88367-116">定義使用自訂控制項視圖定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="88367-116">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="88367-117">CustomEntry for View 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="88367-117">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="88367-118">定義自訂控制項定義的控制項。</span><span class="sxs-lookup"><span data-stu-id="88367-118">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="88367-119">父元素</span><span class="sxs-lookup"><span data-stu-id="88367-119">Parent Elements</span></span>

|<span data-ttu-id="88367-120">元素</span><span class="sxs-lookup"><span data-stu-id="88367-120">Element</span></span>|<span data-ttu-id="88367-121">描述</span><span class="sxs-lookup"><span data-stu-id="88367-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="88367-122">CustomControl for View 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="88367-122">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="88367-123">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="88367-123">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="88367-124">自訂控制項視圖必須指定一或多個定義。</span><span class="sxs-lookup"><span data-stu-id="88367-124">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="88367-125">備註</span><span class="sxs-lookup"><span data-stu-id="88367-125">Remarks</span></span>

<span data-ttu-id="88367-126">在大部分的情況下，每個自訂控制項視圖都只需要一個定義，但是如果您想要使用相同的視圖來顯示不同的 .NET 物件，則可能會有多個定義。</span><span class="sxs-lookup"><span data-stu-id="88367-126">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="88367-127">在這些情況下，您可以為每個物件或一組物件提供個別的定義。</span><span class="sxs-lookup"><span data-stu-id="88367-127">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="88367-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88367-128">See Also</span></span>

[<span data-ttu-id="88367-129">View 的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="88367-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="88367-130">CustomEntry for View 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="88367-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="88367-131">CustomEntry for View 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="88367-131">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="88367-132">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="88367-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)