---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的 CustomControl 的 CustomEntries 元素 (格式)
description: 檢視之控制項的 CustomControl 的 CustomEntries 元素 (格式)
ms.openlocfilehash: 43187294a407d08f765f8c42aba25d13dba6d901
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652382"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="7c1cc-103">檢視之控制項的 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7c1cc-103">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="7c1cc-104">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="7c1cc-104">Provides the definitions for the control.</span></span> <span data-ttu-id="7c1cc-105">當定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="7c1cc-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="7c1cc-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 專案 (格式) 控制項專案 (格式) 控制項專案 (格式) CustomEntries 元素，用於視圖 (格式的控制項 CustomControl 元素) </span><span class="sxs-lookup"><span data-stu-id="7c1cc-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7c1cc-107">語法</span><span class="sxs-lookup"><span data-stu-id="7c1cc-107">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7c1cc-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7c1cc-108">Attributes and Elements</span></span>

<span data-ttu-id="7c1cc-109">下列章節說明屬性、子專案和元素的父元素 `CustomEntries` 。</span><span class="sxs-lookup"><span data-stu-id="7c1cc-109">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="7c1cc-110">可指定的子專案數目沒有最大限制。</span><span class="sxs-lookup"><span data-stu-id="7c1cc-110">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="7c1cc-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7c1cc-111">Attributes</span></span>

<span data-ttu-id="7c1cc-112">無。</span><span class="sxs-lookup"><span data-stu-id="7c1cc-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7c1cc-113">子元素</span><span class="sxs-lookup"><span data-stu-id="7c1cc-113">Child Elements</span></span>

|<span data-ttu-id="7c1cc-114">元素</span><span class="sxs-lookup"><span data-stu-id="7c1cc-114">Element</span></span>|<span data-ttu-id="7c1cc-115">描述</span><span class="sxs-lookup"><span data-stu-id="7c1cc-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7c1cc-116">檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7c1cc-116">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="7c1cc-117">必要元素。</span><span class="sxs-lookup"><span data-stu-id="7c1cc-117">Required element.</span></span><br /><br /> <span data-ttu-id="7c1cc-118">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="7c1cc-118">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7c1cc-119">父項目</span><span class="sxs-lookup"><span data-stu-id="7c1cc-119">Parent Elements</span></span>

|<span data-ttu-id="7c1cc-120">元素</span><span class="sxs-lookup"><span data-stu-id="7c1cc-120">Element</span></span>|<span data-ttu-id="7c1cc-121">描述</span><span class="sxs-lookup"><span data-stu-id="7c1cc-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7c1cc-122">檢視之控制項的控制項 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7c1cc-122">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="7c1cc-123">定義視圖所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="7c1cc-123">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7c1cc-124">備註</span><span class="sxs-lookup"><span data-stu-id="7c1cc-124">Remarks</span></span>

<span data-ttu-id="7c1cc-125">在大部分的情況下，控制項只會在單一元素中指定一個定義 `CustomEntry` 。</span><span class="sxs-lookup"><span data-stu-id="7c1cc-125">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="7c1cc-126">但是，如果您想要使用相同的控制項來顯示不同的 .NET 物件，就可以提供多個定義。</span><span class="sxs-lookup"><span data-stu-id="7c1cc-126">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="7c1cc-127">在這些情況下，您可以 `CustomEntry` 為每個物件或一組物件定義一個元素。</span><span class="sxs-lookup"><span data-stu-id="7c1cc-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c1cc-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c1cc-128">See Also</span></span>

[<span data-ttu-id="7c1cc-129">檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7c1cc-129">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="7c1cc-130">檢視之控制項的控制項 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7c1cc-130">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="7c1cc-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="7c1cc-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
