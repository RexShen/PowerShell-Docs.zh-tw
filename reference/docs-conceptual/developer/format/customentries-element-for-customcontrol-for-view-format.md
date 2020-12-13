---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之 CustomControl 的 CustomEntries 元素 (格式)
description: 檢視之 CustomControl 的 CustomEntries 元素 (格式)
ms.openlocfilehash: 6e757bccdface2503667f8786462a2b43134a07d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649976"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="ff80b-103">檢視之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ff80b-103">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="ff80b-104">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="ff80b-104">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="ff80b-105">自訂控制項視圖必須指定一或多個定義。</span><span class="sxs-lookup"><span data-stu-id="ff80b-105">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="ff80b-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) CustomControl 元素 (format) CustomEntries 元素 for CustomControl for View (格式) </span><span class="sxs-lookup"><span data-stu-id="ff80b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ff80b-107">語法</span><span class="sxs-lookup"><span data-stu-id="ff80b-107">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ff80b-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ff80b-108">Attributes and Elements</span></span>

<span data-ttu-id="ff80b-109">下列各節說明屬性、子專案和元素的父元素 `CustomControlEntries` 。</span><span class="sxs-lookup"><span data-stu-id="ff80b-109">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="ff80b-110">您必須指定一個或多個子項目。</span><span class="sxs-lookup"><span data-stu-id="ff80b-110">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ff80b-111">屬性</span><span class="sxs-lookup"><span data-stu-id="ff80b-111">Attributes</span></span>

<span data-ttu-id="ff80b-112">無。</span><span class="sxs-lookup"><span data-stu-id="ff80b-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ff80b-113">子元素</span><span class="sxs-lookup"><span data-stu-id="ff80b-113">Child Elements</span></span>

|<span data-ttu-id="ff80b-114">元素</span><span class="sxs-lookup"><span data-stu-id="ff80b-114">Element</span></span>|<span data-ttu-id="ff80b-115">描述</span><span class="sxs-lookup"><span data-stu-id="ff80b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ff80b-116">適用于 CustomEntries 的 CustomEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="ff80b-116">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="ff80b-117">必要元素。</span><span class="sxs-lookup"><span data-stu-id="ff80b-117">Required element.</span></span><br /><br /> <span data-ttu-id="ff80b-118">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="ff80b-118">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ff80b-119">父項目</span><span class="sxs-lookup"><span data-stu-id="ff80b-119">Parent Elements</span></span>

|<span data-ttu-id="ff80b-120">元素</span><span class="sxs-lookup"><span data-stu-id="ff80b-120">Element</span></span>|<span data-ttu-id="ff80b-121">描述</span><span class="sxs-lookup"><span data-stu-id="ff80b-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ff80b-122">檢視的 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ff80b-122">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="ff80b-123">必要元素。</span><span class="sxs-lookup"><span data-stu-id="ff80b-123">Required element.</span></span><br /><br /> <span data-ttu-id="ff80b-124">定義視圖的自訂控制項格式。</span><span class="sxs-lookup"><span data-stu-id="ff80b-124">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ff80b-125">備註</span><span class="sxs-lookup"><span data-stu-id="ff80b-125">Remarks</span></span>

<span data-ttu-id="ff80b-126">在大部分的情況下，控制項只有一個定義，定義在單一專案中 `CustomEntry` 。</span><span class="sxs-lookup"><span data-stu-id="ff80b-126">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="ff80b-127">但是，如果您想要使用相同的控制項來顯示不同的 .NET 物件，則可以有多個定義。</span><span class="sxs-lookup"><span data-stu-id="ff80b-127">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="ff80b-128">在這些情況下，您可以 `CustomEntry` 為每個物件或一組物件定義一個元素。</span><span class="sxs-lookup"><span data-stu-id="ff80b-128">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff80b-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff80b-129">See Also</span></span>

[<span data-ttu-id="ff80b-130">檢視的 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ff80b-130">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="ff80b-131">適用于 CustomEntries 的 CustomEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="ff80b-131">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ff80b-132">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="ff80b-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
