---
title: 控制控制項的項目，組態 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066784"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="3992f-102">設定之控制項的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3992f-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="3992f-103">定義可供的格式化檔案以及用來參考的控制項名稱的所有檢視通用控制項。</span><span class="sxs-lookup"><span data-stu-id="3992f-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="3992f-104">組態 （格式） 的組態 （格式） 的控制項的控制項項目的組態項目 （格式） 的控制項項目</span><span class="sxs-lookup"><span data-stu-id="3992f-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3992f-105">語法</span><span class="sxs-lookup"><span data-stu-id="3992f-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3992f-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3992f-106">Attributes and Elements</span></span>

<span data-ttu-id="3992f-107">下列各節說明屬性、 子項目和父項目，如`Control`項目。</span><span class="sxs-lookup"><span data-stu-id="3992f-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="3992f-108">您必須指定其中一個每個子項目。</span><span class="sxs-lookup"><span data-stu-id="3992f-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3992f-109">屬性</span><span class="sxs-lookup"><span data-stu-id="3992f-109">Attributes</span></span>

<span data-ttu-id="3992f-110">無。</span><span class="sxs-lookup"><span data-stu-id="3992f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3992f-111">子元素</span><span class="sxs-lookup"><span data-stu-id="3992f-111">Child Elements</span></span>

|<span data-ttu-id="3992f-112">元素</span><span class="sxs-lookup"><span data-stu-id="3992f-112">Element</span></span>|<span data-ttu-id="3992f-113">描述</span><span class="sxs-lookup"><span data-stu-id="3992f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3992f-114">CustomControl 組態 （格式） 的控制項的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="3992f-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="3992f-115">必要項目。</span><span class="sxs-lookup"><span data-stu-id="3992f-115">Required element.</span></span><br /><br /> <span data-ttu-id="3992f-116">定義控制項。</span><span class="sxs-lookup"><span data-stu-id="3992f-116">Defines the control.</span></span>|
|[<span data-ttu-id="3992f-117">組態 （格式） 的控制項的 name 元素</span><span class="sxs-lookup"><span data-stu-id="3992f-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="3992f-118">必要項目。</span><span class="sxs-lookup"><span data-stu-id="3992f-118">Required element.</span></span><br /><br /> <span data-ttu-id="3992f-119">指定用來參考該控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="3992f-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3992f-120">父項目</span><span class="sxs-lookup"><span data-stu-id="3992f-120">Parent Elements</span></span>

|<span data-ttu-id="3992f-121">項目</span><span class="sxs-lookup"><span data-stu-id="3992f-121">Element</span></span>|<span data-ttu-id="3992f-122">描述</span><span class="sxs-lookup"><span data-stu-id="3992f-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3992f-123">組態 （格式） 的 controls 項目</span><span class="sxs-lookup"><span data-stu-id="3992f-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="3992f-124">定義可用的格式化檔案的所有檢視，或其他控制項的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="3992f-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3992f-125">備註</span><span class="sxs-lookup"><span data-stu-id="3992f-125">Remarks</span></span>

<span data-ttu-id="3992f-126">提供給這個控制項的名稱可以在下列項目中參考：</span><span class="sxs-lookup"><span data-stu-id="3992f-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="3992f-127">ExpressionBinding CustomItem （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="3992f-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="3992f-128">GroupBy View(Format) 的項目</span><span class="sxs-lookup"><span data-stu-id="3992f-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="3992f-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3992f-129">See Also</span></span>

[<span data-ttu-id="3992f-130">組態 （格式） 的 controls 項目</span><span class="sxs-lookup"><span data-stu-id="3992f-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="3992f-131">CustomControl 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="3992f-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="3992f-132">ExpressionBinding CustomItem （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="3992f-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="3992f-133">GroupBy View(Format) 的項目</span><span class="sxs-lookup"><span data-stu-id="3992f-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="3992f-134">組態 （格式） 的控制項的控制項的 name 元素</span><span class="sxs-lookup"><span data-stu-id="3992f-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="3992f-135">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="3992f-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
