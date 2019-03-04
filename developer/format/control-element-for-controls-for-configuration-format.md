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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858884"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="86bc2-102">設定之控制項的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="86bc2-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="86bc2-103">定義可供的格式化檔案以及用來參考的控制項名稱的所有檢視通用控制項。</span><span class="sxs-lookup"><span data-stu-id="86bc2-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="86bc2-104">組態 （格式） 的組態 （格式） 的控制項的控制項項目的組態項目 （格式） 的控制項項目</span><span class="sxs-lookup"><span data-stu-id="86bc2-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="86bc2-105">語法</span><span class="sxs-lookup"><span data-stu-id="86bc2-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="86bc2-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="86bc2-106">Attributes and Elements</span></span>

<span data-ttu-id="86bc2-107">下列各節說明屬性、 子項目和父項目，如`Control`項目。</span><span class="sxs-lookup"><span data-stu-id="86bc2-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="86bc2-108">您必須指定其中一個每個子項目。</span><span class="sxs-lookup"><span data-stu-id="86bc2-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="86bc2-109">屬性</span><span class="sxs-lookup"><span data-stu-id="86bc2-109">Attributes</span></span>

<span data-ttu-id="86bc2-110">無。</span><span class="sxs-lookup"><span data-stu-id="86bc2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="86bc2-111">子元素</span><span class="sxs-lookup"><span data-stu-id="86bc2-111">Child Elements</span></span>

|<span data-ttu-id="86bc2-112">元素</span><span class="sxs-lookup"><span data-stu-id="86bc2-112">Element</span></span>|<span data-ttu-id="86bc2-113">描述</span><span class="sxs-lookup"><span data-stu-id="86bc2-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86bc2-114">CustomControl 組態 （格式） 的控制項的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="86bc2-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="86bc2-115">必要項目。</span><span class="sxs-lookup"><span data-stu-id="86bc2-115">Required element.</span></span><br /><br /> <span data-ttu-id="86bc2-116">定義控制項。</span><span class="sxs-lookup"><span data-stu-id="86bc2-116">Defines the control.</span></span>|
|[<span data-ttu-id="86bc2-117">組態 （格式） 的控制項的 name 元素</span><span class="sxs-lookup"><span data-stu-id="86bc2-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="86bc2-118">必要項目。</span><span class="sxs-lookup"><span data-stu-id="86bc2-118">Required element.</span></span><br /><br /> <span data-ttu-id="86bc2-119">指定用來參考該控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="86bc2-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="86bc2-120">父元素</span><span class="sxs-lookup"><span data-stu-id="86bc2-120">Parent Elements</span></span>

|<span data-ttu-id="86bc2-121">元素</span><span class="sxs-lookup"><span data-stu-id="86bc2-121">Element</span></span>|<span data-ttu-id="86bc2-122">描述</span><span class="sxs-lookup"><span data-stu-id="86bc2-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86bc2-123">組態 （格式） 的 controls 項目</span><span class="sxs-lookup"><span data-stu-id="86bc2-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="86bc2-124">定義可用的格式化檔案的所有檢視，或其他控制項的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="86bc2-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="86bc2-125">備註</span><span class="sxs-lookup"><span data-stu-id="86bc2-125">Remarks</span></span>

<span data-ttu-id="86bc2-126">提供給這個控制項的名稱可以在下列項目中參考：</span><span class="sxs-lookup"><span data-stu-id="86bc2-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="86bc2-127">ExpressionBinding CustomItem （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="86bc2-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="86bc2-128">GroupBy View(Format) 的項目</span><span class="sxs-lookup"><span data-stu-id="86bc2-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="86bc2-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86bc2-129">See Also</span></span>

[<span data-ttu-id="86bc2-130">組態 （格式） 的 controls 項目</span><span class="sxs-lookup"><span data-stu-id="86bc2-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="86bc2-131">CustomControl 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="86bc2-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="86bc2-132">ExpressionBinding CustomItem （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="86bc2-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="86bc2-133">GroupBy View(Format) 的項目</span><span class="sxs-lookup"><span data-stu-id="86bc2-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="86bc2-134">組態 （格式） 的控制項的控制項的 name 元素</span><span class="sxs-lookup"><span data-stu-id="86bc2-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="86bc2-135">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="86bc2-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
