---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視的 CustomControl 元素 (格式)
description: 檢視的 CustomControl 元素 (格式)
ms.openlocfilehash: 41352be55f0c03b2eaca0dbe2d7345e7cf804a7c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655470"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="dada7-103">檢視的 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dada7-103">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="dada7-104">定義視圖的自訂控制項格式。</span><span class="sxs-lookup"><span data-stu-id="dada7-104">Defines a custom control format for the view.</span></span>

<span data-ttu-id="dada7-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) CustomControl 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="dada7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dada7-106">語法</span><span class="sxs-lookup"><span data-stu-id="dada7-106">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dada7-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dada7-107">Attributes and Elements</span></span>

<span data-ttu-id="dada7-108">下列各節說明屬性、子專案和元素的父元素 `CustomControl` 。</span><span class="sxs-lookup"><span data-stu-id="dada7-108">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="dada7-109">您必須指定一個子項目。</span><span class="sxs-lookup"><span data-stu-id="dada7-109">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dada7-110">屬性</span><span class="sxs-lookup"><span data-stu-id="dada7-110">Attributes</span></span>

<span data-ttu-id="dada7-111">無。</span><span class="sxs-lookup"><span data-stu-id="dada7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dada7-112">子元素</span><span class="sxs-lookup"><span data-stu-id="dada7-112">Child Elements</span></span>

|<span data-ttu-id="dada7-113">元素</span><span class="sxs-lookup"><span data-stu-id="dada7-113">Element</span></span>|<span data-ttu-id="dada7-114">描述</span><span class="sxs-lookup"><span data-stu-id="dada7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dada7-115">檢視之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dada7-115">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="dada7-116">必要元素。</span><span class="sxs-lookup"><span data-stu-id="dada7-116">Required element.</span></span><br /><br /> <span data-ttu-id="dada7-117">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="dada7-117">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dada7-118">父項目</span><span class="sxs-lookup"><span data-stu-id="dada7-118">Parent Elements</span></span>

|<span data-ttu-id="dada7-119">元素</span><span class="sxs-lookup"><span data-stu-id="dada7-119">Element</span></span>|<span data-ttu-id="dada7-120">描述</span><span class="sxs-lookup"><span data-stu-id="dada7-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dada7-121">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dada7-121">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="dada7-122">定義用來顯示一或多個 .NET 物件的視圖。</span><span class="sxs-lookup"><span data-stu-id="dada7-122">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dada7-123">備註</span><span class="sxs-lookup"><span data-stu-id="dada7-123">Remarks</span></span>

<span data-ttu-id="dada7-124">在大部分的情況下，每個控制項視圖都只需要一個定義，但如果您想要使用相同的視圖來顯示不同的 .NET 物件，就可以提供多個定義。</span><span class="sxs-lookup"><span data-stu-id="dada7-124">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="dada7-125">在這些情況下，您可以為每個物件或一組物件提供個別的定義。</span><span class="sxs-lookup"><span data-stu-id="dada7-125">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="dada7-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dada7-126">See Also</span></span>

[<span data-ttu-id="dada7-127">檢視之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dada7-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="dada7-128">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dada7-128">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="dada7-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="dada7-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
