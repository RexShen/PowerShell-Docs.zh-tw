---
title: Configuration 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363497"
---
# <a name="configuration-element-format"></a><span data-ttu-id="76cd3-102">設定元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="76cd3-102">Configuration Element (Format)</span></span>

<span data-ttu-id="76cd3-103">代表格式化檔案的最上層元素。</span><span class="sxs-lookup"><span data-stu-id="76cd3-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="76cd3-104">Configuration 元素</span><span class="sxs-lookup"><span data-stu-id="76cd3-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="76cd3-105">語法</span><span class="sxs-lookup"><span data-stu-id="76cd3-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="76cd3-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="76cd3-106">Attributes and Elements</span></span>

<span data-ttu-id="76cd3-107">下列各節說明屬性、子專案，以及 `Configuration` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="76cd3-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="76cd3-108">此元素必須是每個格式化檔案的根項目，且此元素必須包含至少一個子專案。</span><span class="sxs-lookup"><span data-stu-id="76cd3-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="76cd3-109">屬性</span><span class="sxs-lookup"><span data-stu-id="76cd3-109">Attributes</span></span>

<span data-ttu-id="76cd3-110">無。</span><span class="sxs-lookup"><span data-stu-id="76cd3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="76cd3-111">子元素</span><span class="sxs-lookup"><span data-stu-id="76cd3-111">Child Elements</span></span>

|<span data-ttu-id="76cd3-112">元素</span><span class="sxs-lookup"><span data-stu-id="76cd3-112">Element</span></span>|<span data-ttu-id="76cd3-113">描述</span><span class="sxs-lookup"><span data-stu-id="76cd3-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="76cd3-114">設定的 Controls 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="76cd3-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="76cd3-115">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="76cd3-115">Optional element.</span></span><br /><br /> <span data-ttu-id="76cd3-116">定義可供格式檔案的所有視圖使用的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="76cd3-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="76cd3-117">DefaultSettings 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="76cd3-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="76cd3-118">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="76cd3-118">Optional element.</span></span><br /><br /> <span data-ttu-id="76cd3-119">定義套用至格式化檔案所有視圖的一般設定。</span><span class="sxs-lookup"><span data-stu-id="76cd3-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="76cd3-120">SelectionSets 元素格式</span><span class="sxs-lookup"><span data-stu-id="76cd3-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="76cd3-121">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="76cd3-121">Optional element.</span></span><br /><br /> <span data-ttu-id="76cd3-122">定義一組通用的 .NET 物件，可供格式化檔案的所有視圖使用。</span><span class="sxs-lookup"><span data-stu-id="76cd3-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="76cd3-123">ViewDefinitions 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="76cd3-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="76cd3-124">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="76cd3-124">Optional element.</span></span><br /><br /> <span data-ttu-id="76cd3-125">定義用來顯示物件的視圖。</span><span class="sxs-lookup"><span data-stu-id="76cd3-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="76cd3-126">父元素</span><span class="sxs-lookup"><span data-stu-id="76cd3-126">Parent Elements</span></span>

<span data-ttu-id="76cd3-127">無。</span><span class="sxs-lookup"><span data-stu-id="76cd3-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="76cd3-128">備註</span><span class="sxs-lookup"><span data-stu-id="76cd3-128">Remarks</span></span>

<span data-ttu-id="76cd3-129">格式化檔案會定義物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="76cd3-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="76cd3-130">在大部分的情況下，這個根項目包含[ViewDefinitions](./viewdefinitions-element-format.md)元素，可定義格式檔案的資料表、清單和寬視圖。</span><span class="sxs-lookup"><span data-stu-id="76cd3-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="76cd3-131">除了 view 定義以外，格式檔案也可以定義這些視圖可以使用的一般選取範圍、設定和控制項。</span><span class="sxs-lookup"><span data-stu-id="76cd3-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="76cd3-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76cd3-132">See Also</span></span>

[<span data-ttu-id="76cd3-133">設定的 Controls 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="76cd3-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="76cd3-134">DefaultSettings 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="76cd3-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="76cd3-135">SelectionSets 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="76cd3-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="76cd3-136">ViewDefinitions 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="76cd3-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="76cd3-137">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="76cd3-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
