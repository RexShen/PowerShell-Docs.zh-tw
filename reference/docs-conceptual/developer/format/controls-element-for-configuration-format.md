---
title: 設定 (格式) 的 Controls 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 44b9db0d3523e5e9086da9911882b258a2a54ca6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783784"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="d186a-102">設定的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d186a-102">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="d186a-103">定義可供格式檔案的所有視圖使用的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="d186a-103">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="d186a-104">Configuration 元素 (格式) Controls 設定 (格式的元素) </span><span class="sxs-lookup"><span data-stu-id="d186a-104">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d186a-105">語法</span><span class="sxs-lookup"><span data-stu-id="d186a-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d186a-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d186a-106">Attributes and Elements</span></span>

<span data-ttu-id="d186a-107">下列各節說明屬性、子專案和元素的父元素 `Controls` 。</span><span class="sxs-lookup"><span data-stu-id="d186a-107">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d186a-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d186a-108">Attributes</span></span>

<span data-ttu-id="d186a-109">無。</span><span class="sxs-lookup"><span data-stu-id="d186a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d186a-110">子元素</span><span class="sxs-lookup"><span data-stu-id="d186a-110">Child Elements</span></span>

|<span data-ttu-id="d186a-111">元素</span><span class="sxs-lookup"><span data-stu-id="d186a-111">Element</span></span>|<span data-ttu-id="d186a-112">描述</span><span class="sxs-lookup"><span data-stu-id="d186a-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d186a-113">設定之控制項的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d186a-113">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="d186a-114">必要元素。</span><span class="sxs-lookup"><span data-stu-id="d186a-114">Required element.</span></span><br /><br /> <span data-ttu-id="d186a-115">定義可供格式檔案的所有視圖使用的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="d186a-115">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d186a-116">父項目</span><span class="sxs-lookup"><span data-stu-id="d186a-116">Parent Elements</span></span>

|<span data-ttu-id="d186a-117">元素</span><span class="sxs-lookup"><span data-stu-id="d186a-117">Element</span></span>|<span data-ttu-id="d186a-118">描述</span><span class="sxs-lookup"><span data-stu-id="d186a-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d186a-119">設定元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d186a-119">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="d186a-120">代表格式化檔案的最上層元素。</span><span class="sxs-lookup"><span data-stu-id="d186a-120">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d186a-121">備註</span><span class="sxs-lookup"><span data-stu-id="d186a-121">Remarks</span></span>

<span data-ttu-id="d186a-122">您可以建立任意數目的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="d186a-122">You can create any number of common controls.</span></span> <span data-ttu-id="d186a-123">您必須針對每個控制項指定用來參考控制項的名稱，以及控制項的元件。</span><span class="sxs-lookup"><span data-stu-id="d186a-123">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="d186a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d186a-124">See Also</span></span>

[<span data-ttu-id="d186a-125">設定元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d186a-125">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="d186a-126">設定之控制項的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d186a-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="d186a-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="d186a-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
