---
title: 設定的 Controls 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368997"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="76caf-102">設定的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="76caf-102">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="76caf-103">定義可供格式檔案的所有視圖使用的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="76caf-103">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="76caf-104">Configuration 元素（格式）控制設定的元素（格式）</span><span class="sxs-lookup"><span data-stu-id="76caf-104">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="76caf-105">語法</span><span class="sxs-lookup"><span data-stu-id="76caf-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="76caf-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="76caf-106">Attributes and Elements</span></span>

<span data-ttu-id="76caf-107">下列各節說明屬性、子專案，以及 `Controls` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="76caf-107">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="76caf-108">屬性</span><span class="sxs-lookup"><span data-stu-id="76caf-108">Attributes</span></span>

<span data-ttu-id="76caf-109">無。</span><span class="sxs-lookup"><span data-stu-id="76caf-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="76caf-110">子元素</span><span class="sxs-lookup"><span data-stu-id="76caf-110">Child Elements</span></span>

|<span data-ttu-id="76caf-111">元素</span><span class="sxs-lookup"><span data-stu-id="76caf-111">Element</span></span>|<span data-ttu-id="76caf-112">描述</span><span class="sxs-lookup"><span data-stu-id="76caf-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="76caf-113">設定之控制項的控制項元素（格式）</span><span class="sxs-lookup"><span data-stu-id="76caf-113">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="76caf-114">必要元素。</span><span class="sxs-lookup"><span data-stu-id="76caf-114">Required element.</span></span><br /><br /> <span data-ttu-id="76caf-115">定義可供格式檔案的所有視圖使用的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="76caf-115">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="76caf-116">父元素</span><span class="sxs-lookup"><span data-stu-id="76caf-116">Parent Elements</span></span>

|<span data-ttu-id="76caf-117">元素</span><span class="sxs-lookup"><span data-stu-id="76caf-117">Element</span></span>|<span data-ttu-id="76caf-118">描述</span><span class="sxs-lookup"><span data-stu-id="76caf-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="76caf-119">Configuration 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="76caf-119">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="76caf-120">代表格式化檔案的最上層元素。</span><span class="sxs-lookup"><span data-stu-id="76caf-120">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="76caf-121">備註</span><span class="sxs-lookup"><span data-stu-id="76caf-121">Remarks</span></span>

<span data-ttu-id="76caf-122">您可以建立任意數目的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="76caf-122">You can create any number of common controls.</span></span> <span data-ttu-id="76caf-123">您必須針對每個控制項指定用來參考控制項的名稱，以及控制項的元件。</span><span class="sxs-lookup"><span data-stu-id="76caf-123">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="76caf-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76caf-124">See Also</span></span>

[<span data-ttu-id="76caf-125">Configuration 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="76caf-125">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="76caf-126">設定之控制項的控制項元素（格式）</span><span class="sxs-lookup"><span data-stu-id="76caf-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="76caf-127">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="76caf-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
