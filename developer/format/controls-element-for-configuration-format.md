---
title: 組態 （格式） 的 controls 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861174"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="7aa91-102">設定的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7aa91-102">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="7aa91-103">定義可由格式檔案的所有檢視通用控制項。</span><span class="sxs-lookup"><span data-stu-id="7aa91-103">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="7aa91-104">組態 （格式） 的組態項目 （格式） 的控制項項目</span><span class="sxs-lookup"><span data-stu-id="7aa91-104">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7aa91-105">語法</span><span class="sxs-lookup"><span data-stu-id="7aa91-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7aa91-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="7aa91-106">Attributes and Elements</span></span>

<span data-ttu-id="7aa91-107">下列各節說明屬性、 子項目和父項目`Controls`項目。</span><span class="sxs-lookup"><span data-stu-id="7aa91-107">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7aa91-108">屬性</span><span class="sxs-lookup"><span data-stu-id="7aa91-108">Attributes</span></span>

<span data-ttu-id="7aa91-109">無。</span><span class="sxs-lookup"><span data-stu-id="7aa91-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7aa91-110">子元素</span><span class="sxs-lookup"><span data-stu-id="7aa91-110">Child Elements</span></span>

|<span data-ttu-id="7aa91-111">元素</span><span class="sxs-lookup"><span data-stu-id="7aa91-111">Element</span></span>|<span data-ttu-id="7aa91-112">描述</span><span class="sxs-lookup"><span data-stu-id="7aa91-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7aa91-113">組態 （格式） 的控制項的控制項項目</span><span class="sxs-lookup"><span data-stu-id="7aa91-113">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="7aa91-114">必要項目。</span><span class="sxs-lookup"><span data-stu-id="7aa91-114">Required element.</span></span><br /><br /> <span data-ttu-id="7aa91-115">定義可由格式檔案的所有檢視通用控制項。</span><span class="sxs-lookup"><span data-stu-id="7aa91-115">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7aa91-116">父元素</span><span class="sxs-lookup"><span data-stu-id="7aa91-116">Parent Elements</span></span>

|<span data-ttu-id="7aa91-117">元素</span><span class="sxs-lookup"><span data-stu-id="7aa91-117">Element</span></span>|<span data-ttu-id="7aa91-118">描述</span><span class="sxs-lookup"><span data-stu-id="7aa91-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7aa91-119">組態項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="7aa91-119">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="7aa91-120">表示格式化檔案的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="7aa91-120">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7aa91-121">備註</span><span class="sxs-lookup"><span data-stu-id="7aa91-121">Remarks</span></span>

<span data-ttu-id="7aa91-122">您可以建立任意數目的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="7aa91-122">You can create any number of common controls.</span></span> <span data-ttu-id="7aa91-123">針對每個控制項中，您必須指定用來參考控制項和控制項的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="7aa91-123">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="7aa91-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7aa91-124">See Also</span></span>

[<span data-ttu-id="7aa91-125">組態項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="7aa91-125">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="7aa91-126">組態 （格式） 的控制項的控制項項目</span><span class="sxs-lookup"><span data-stu-id="7aa91-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="7aa91-127">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="7aa91-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
