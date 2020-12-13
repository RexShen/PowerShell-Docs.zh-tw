---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 CustomControl 的 CustomEntries 元素 (格式)
description: 設定之控制項的 CustomControl 的 CustomEntries 元素 (格式)
ms.openlocfilehash: 86c2b517d0d7075a355a3190a14e25d9dd4fe374
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655396"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="dd655-103">設定之控制項的 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dd655-103">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="dd655-104">提供通用控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="dd655-104">Provides the definitions of a common control.</span></span> <span data-ttu-id="dd655-105">當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="dd655-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="dd655-106">設定元素 (格式) 控制項的設定元素 (格式) 控制項的設定 (格式) CustomControl 元素，用於 CustomControl 的設定 (格式) </span><span class="sxs-lookup"><span data-stu-id="dd655-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dd655-107">語法</span><span class="sxs-lookup"><span data-stu-id="dd655-107">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="dd655-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dd655-108">Attributes and Elements</span></span>

<span data-ttu-id="dd655-109">下列各節說明屬性、子專案和元素的父元素 `CustomEntries` 。</span><span class="sxs-lookup"><span data-stu-id="dd655-109">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="dd655-110">您必須指定一個或多個子項目。</span><span class="sxs-lookup"><span data-stu-id="dd655-110">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="dd655-111">屬性</span><span class="sxs-lookup"><span data-stu-id="dd655-111">Attributes</span></span>

<span data-ttu-id="dd655-112">無。</span><span class="sxs-lookup"><span data-stu-id="dd655-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dd655-113">子元素</span><span class="sxs-lookup"><span data-stu-id="dd655-113">Child Elements</span></span>

|<span data-ttu-id="dd655-114">元素</span><span class="sxs-lookup"><span data-stu-id="dd655-114">Element</span></span>|<span data-ttu-id="dd655-115">描述</span><span class="sxs-lookup"><span data-stu-id="dd655-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dd655-116">設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dd655-116">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="dd655-117">提供通用控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="dd655-117">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dd655-118">父項目</span><span class="sxs-lookup"><span data-stu-id="dd655-118">Parent Elements</span></span>

|<span data-ttu-id="dd655-119">元素</span><span class="sxs-lookup"><span data-stu-id="dd655-119">Element</span></span>|<span data-ttu-id="dd655-120">描述</span><span class="sxs-lookup"><span data-stu-id="dd655-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dd655-121">CustomControl 元素，可控制設定 (格式) </span><span class="sxs-lookup"><span data-stu-id="dd655-121">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="dd655-122">定義通用控制項。</span><span class="sxs-lookup"><span data-stu-id="dd655-122">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dd655-123">備註</span><span class="sxs-lookup"><span data-stu-id="dd655-123">Remarks</span></span>

<span data-ttu-id="dd655-124">在大部分的情況下，控制項只有一個定義，定義在單一專案中 `CustomEntry` 。</span><span class="sxs-lookup"><span data-stu-id="dd655-124">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="dd655-125">但是，如果您想要使用相同的控制項來顯示不同的 .NET 物件，則可以有多個定義。</span><span class="sxs-lookup"><span data-stu-id="dd655-125">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="dd655-126">在這些情況下，您可以 `CustomEntry` 為每個物件或一組物件定義一個元素。</span><span class="sxs-lookup"><span data-stu-id="dd655-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd655-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd655-127">See Also</span></span>

[<span data-ttu-id="dd655-128">CustomControl 元素，可控制設定 (格式) </span><span class="sxs-lookup"><span data-stu-id="dd655-128">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="dd655-129">設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dd655-129">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="dd655-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="dd655-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
