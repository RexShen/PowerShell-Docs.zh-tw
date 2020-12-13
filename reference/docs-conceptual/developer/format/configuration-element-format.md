---
ms.date: 09/13/2016
ms.topic: reference
title: 設定元素 (格式)
description: 設定元素 (格式)
ms.openlocfilehash: 0524736d40dd7a7acb0b6fb61d1438b75672c240
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655685"
---
# <a name="configuration-element-format"></a><span data-ttu-id="e2fec-103">設定元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e2fec-103">Configuration Element (Format)</span></span>

<span data-ttu-id="e2fec-104">代表格式化檔案的最上層元素。</span><span class="sxs-lookup"><span data-stu-id="e2fec-104">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="e2fec-105">組態元素</span><span class="sxs-lookup"><span data-stu-id="e2fec-105">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="e2fec-106">語法</span><span class="sxs-lookup"><span data-stu-id="e2fec-106">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="e2fec-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e2fec-107">Attributes and Elements</span></span>

<span data-ttu-id="e2fec-108">下列章節說明屬性、子專案和元素的父元素 `Configuration` 。</span><span class="sxs-lookup"><span data-stu-id="e2fec-108">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="e2fec-109">這個元素必須是每個格式化檔案的根項目，而且此元素必須包含至少一個子項目。</span><span class="sxs-lookup"><span data-stu-id="e2fec-109">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e2fec-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e2fec-110">Attributes</span></span>

<span data-ttu-id="e2fec-111">無。</span><span class="sxs-lookup"><span data-stu-id="e2fec-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e2fec-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e2fec-112">Child Elements</span></span>

|<span data-ttu-id="e2fec-113">元素</span><span class="sxs-lookup"><span data-stu-id="e2fec-113">Element</span></span>|<span data-ttu-id="e2fec-114">描述</span><span class="sxs-lookup"><span data-stu-id="e2fec-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e2fec-115">設定的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e2fec-115">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="e2fec-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e2fec-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e2fec-117">定義可供格式化檔案的所有視圖使用的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="e2fec-117">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="e2fec-118">DefaultSettings 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e2fec-118">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="e2fec-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e2fec-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e2fec-120">定義適用于格式檔案所有視圖的一般設定。</span><span class="sxs-lookup"><span data-stu-id="e2fec-120">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="e2fec-121">SelectionSets 元素格式</span><span class="sxs-lookup"><span data-stu-id="e2fec-121">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="e2fec-122">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e2fec-122">Optional element.</span></span><br /><br /> <span data-ttu-id="e2fec-123">定義可供格式化檔案的所有視圖使用的通用 .NET 物件集。</span><span class="sxs-lookup"><span data-stu-id="e2fec-123">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="e2fec-124">ViewDefinitions 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e2fec-124">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="e2fec-125">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e2fec-125">Optional element.</span></span><br /><br /> <span data-ttu-id="e2fec-126">定義用來顯示物件的視圖。</span><span class="sxs-lookup"><span data-stu-id="e2fec-126">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e2fec-127">父項目</span><span class="sxs-lookup"><span data-stu-id="e2fec-127">Parent Elements</span></span>

<span data-ttu-id="e2fec-128">無。</span><span class="sxs-lookup"><span data-stu-id="e2fec-128">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="e2fec-129">備註</span><span class="sxs-lookup"><span data-stu-id="e2fec-129">Remarks</span></span>

<span data-ttu-id="e2fec-130">格式化檔案會定義物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="e2fec-130">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="e2fec-131">在大部分的情況下，此根項目包含定義格式檔案之資料表、清單和寬視圖的 [ViewDefinitions](./viewdefinitions-element-format.md) 專案。</span><span class="sxs-lookup"><span data-stu-id="e2fec-131">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="e2fec-132">除了 view 定義，格式化檔案也可以定義這些視圖可使用的常用選項群組、設定和控制項。</span><span class="sxs-lookup"><span data-stu-id="e2fec-132">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2fec-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2fec-133">See Also</span></span>

[<span data-ttu-id="e2fec-134">設定的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e2fec-134">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="e2fec-135">DefaultSettings 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e2fec-135">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="e2fec-136">SelectionSets 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e2fec-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="e2fec-137">ViewDefinitions 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e2fec-137">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="e2fec-138">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="e2fec-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
