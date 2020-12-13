---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之 CustomControl 的 CustomEntries 元素 (格式)
description: GroupBy 之 CustomControl 的 CustomEntries 元素 (格式)
ms.openlocfilehash: cde59d38b83930cb64a3a0040891783e4ab96723
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666785"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="87ecb-103">GroupBy 之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="87ecb-103">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="87ecb-104">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="87ecb-104">Provides the definitions for the control.</span></span> <span data-ttu-id="87ecb-105">定義如何顯示新的物件群組時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="87ecb-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="87ecb-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 專案 (格式) groupby (格式) CustomEntries 元素，用於 CustomControl 的 groupby (格式) </span><span class="sxs-lookup"><span data-stu-id="87ecb-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="87ecb-107">語法</span><span class="sxs-lookup"><span data-stu-id="87ecb-107">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="87ecb-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="87ecb-108">Attributes and Elements</span></span>

<span data-ttu-id="87ecb-109">下列章節說明屬性、子專案和元素的父元素 `CustomEntries` 。</span><span class="sxs-lookup"><span data-stu-id="87ecb-109">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="87ecb-110">可指定的子專案數目沒有最大限制。</span><span class="sxs-lookup"><span data-stu-id="87ecb-110">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="87ecb-111">屬性</span><span class="sxs-lookup"><span data-stu-id="87ecb-111">Attributes</span></span>

<span data-ttu-id="87ecb-112">無。</span><span class="sxs-lookup"><span data-stu-id="87ecb-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="87ecb-113">子元素</span><span class="sxs-lookup"><span data-stu-id="87ecb-113">Child Elements</span></span>

|<span data-ttu-id="87ecb-114">元素</span><span class="sxs-lookup"><span data-stu-id="87ecb-114">Element</span></span>|<span data-ttu-id="87ecb-115">描述</span><span class="sxs-lookup"><span data-stu-id="87ecb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87ecb-116">GroupBy 之 CustomControl 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="87ecb-116">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="87ecb-117">必要元素。</span><span class="sxs-lookup"><span data-stu-id="87ecb-117">Required element.</span></span><br /><br /> <span data-ttu-id="87ecb-118">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="87ecb-118">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="87ecb-119">父項目</span><span class="sxs-lookup"><span data-stu-id="87ecb-119">Parent Elements</span></span>

|<span data-ttu-id="87ecb-120">元素</span><span class="sxs-lookup"><span data-stu-id="87ecb-120">Element</span></span>|<span data-ttu-id="87ecb-121">描述</span><span class="sxs-lookup"><span data-stu-id="87ecb-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87ecb-122">GroupBy 的 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="87ecb-122">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="87ecb-123">定義顯示新群組的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="87ecb-123">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="87ecb-124">備註</span><span class="sxs-lookup"><span data-stu-id="87ecb-124">Remarks</span></span>

<span data-ttu-id="87ecb-125">在大部分的情況下，控制項只會在單一元素中指定一個定義 `CustomEntry` 。</span><span class="sxs-lookup"><span data-stu-id="87ecb-125">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="87ecb-126">但是，如果您想要使用相同的控制項來顯示不同的群組，則可以提供多個定義。</span><span class="sxs-lookup"><span data-stu-id="87ecb-126">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="87ecb-127">在這些情況下，您可以定義 `CustomEntry` 群組的元素。</span><span class="sxs-lookup"><span data-stu-id="87ecb-127">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="87ecb-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87ecb-128">See Also</span></span>

[<span data-ttu-id="87ecb-129">檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="87ecb-129">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="87ecb-130">GroupBy 的 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="87ecb-130">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="87ecb-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="87ecb-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
