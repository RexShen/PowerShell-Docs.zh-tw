---
ms.date: 09/13/2016
ms.topic: reference
title: 設定的控制項元素 (格式)
description: 設定的控制項元素 (格式)
ms.openlocfilehash: 53f874ddccf3b4f1f0a23aad608e786524bde830
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668094"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="391c2-103">設定的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="391c2-103">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="391c2-104">定義可供格式化檔案的所有視圖使用的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="391c2-104">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="391c2-105">Configuration 元素 (格式) 控制項設定 (格式的元素) </span><span class="sxs-lookup"><span data-stu-id="391c2-105">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="391c2-106">語法</span><span class="sxs-lookup"><span data-stu-id="391c2-106">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="391c2-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="391c2-107">Attributes and Elements</span></span>

<span data-ttu-id="391c2-108">下列章節說明屬性、子專案和元素的父元素 `Controls` 。</span><span class="sxs-lookup"><span data-stu-id="391c2-108">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="391c2-109">屬性</span><span class="sxs-lookup"><span data-stu-id="391c2-109">Attributes</span></span>

<span data-ttu-id="391c2-110">無。</span><span class="sxs-lookup"><span data-stu-id="391c2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="391c2-111">子元素</span><span class="sxs-lookup"><span data-stu-id="391c2-111">Child Elements</span></span>

|<span data-ttu-id="391c2-112">元素</span><span class="sxs-lookup"><span data-stu-id="391c2-112">Element</span></span>|<span data-ttu-id="391c2-113">描述</span><span class="sxs-lookup"><span data-stu-id="391c2-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="391c2-114">設定之控制項的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="391c2-114">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="391c2-115">必要元素。</span><span class="sxs-lookup"><span data-stu-id="391c2-115">Required element.</span></span><br /><br /> <span data-ttu-id="391c2-116">定義可供格式化檔案的所有視圖使用的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="391c2-116">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="391c2-117">父項目</span><span class="sxs-lookup"><span data-stu-id="391c2-117">Parent Elements</span></span>

|<span data-ttu-id="391c2-118">元素</span><span class="sxs-lookup"><span data-stu-id="391c2-118">Element</span></span>|<span data-ttu-id="391c2-119">描述</span><span class="sxs-lookup"><span data-stu-id="391c2-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="391c2-120">設定元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="391c2-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="391c2-121">代表格式化檔案的最上層元素。</span><span class="sxs-lookup"><span data-stu-id="391c2-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="391c2-122">備註</span><span class="sxs-lookup"><span data-stu-id="391c2-122">Remarks</span></span>

<span data-ttu-id="391c2-123">您可以建立任意數目的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="391c2-123">You can create any number of common controls.</span></span> <span data-ttu-id="391c2-124">您必須為每個控制項指定用來參考控制項的名稱，以及控制項的元件。</span><span class="sxs-lookup"><span data-stu-id="391c2-124">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="391c2-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="391c2-125">See Also</span></span>

[<span data-ttu-id="391c2-126">設定元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="391c2-126">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="391c2-127">設定之控制項的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="391c2-127">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="391c2-128">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="391c2-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
