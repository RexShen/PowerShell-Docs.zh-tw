---
title: 設定之控制項的控制項元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369007"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="0c7a6-102">設定之控制項的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0c7a6-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="0c7a6-103">定義可供格式檔案的所有視圖使用的通用控制項，以及用來參考控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c7a6-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="0c7a6-104">Configuration 元素（Format）控制設定之控制項的設定（格式）控制項元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0c7a6-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0c7a6-105">語法</span><span class="sxs-lookup"><span data-stu-id="0c7a6-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0c7a6-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="0c7a6-106">Attributes and Elements</span></span>

<span data-ttu-id="0c7a6-107">下列各節說明屬性、子專案，以及 `Control` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="0c7a6-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="0c7a6-108">您必須只指定其中一個子項目。</span><span class="sxs-lookup"><span data-stu-id="0c7a6-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0c7a6-109">屬性</span><span class="sxs-lookup"><span data-stu-id="0c7a6-109">Attributes</span></span>

<span data-ttu-id="0c7a6-110">無。</span><span class="sxs-lookup"><span data-stu-id="0c7a6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0c7a6-111">子元素</span><span class="sxs-lookup"><span data-stu-id="0c7a6-111">Child Elements</span></span>

|<span data-ttu-id="0c7a6-112">元素</span><span class="sxs-lookup"><span data-stu-id="0c7a6-112">Element</span></span>|<span data-ttu-id="0c7a6-113">描述</span><span class="sxs-lookup"><span data-stu-id="0c7a6-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0c7a6-114">設定之控制項控制項的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0c7a6-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="0c7a6-115">必要元素。</span><span class="sxs-lookup"><span data-stu-id="0c7a6-115">Required element.</span></span><br /><br /> <span data-ttu-id="0c7a6-116">定義控制項。</span><span class="sxs-lookup"><span data-stu-id="0c7a6-116">Defines the control.</span></span>|
|[<span data-ttu-id="0c7a6-117">設定之控制項的名稱元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0c7a6-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="0c7a6-118">必要元素。</span><span class="sxs-lookup"><span data-stu-id="0c7a6-118">Required element.</span></span><br /><br /> <span data-ttu-id="0c7a6-119">指定用來參考控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c7a6-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0c7a6-120">父元素</span><span class="sxs-lookup"><span data-stu-id="0c7a6-120">Parent Elements</span></span>

|<span data-ttu-id="0c7a6-121">元素</span><span class="sxs-lookup"><span data-stu-id="0c7a6-121">Element</span></span>|<span data-ttu-id="0c7a6-122">描述</span><span class="sxs-lookup"><span data-stu-id="0c7a6-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0c7a6-123">設定的控制項元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0c7a6-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="0c7a6-124">定義可供格式檔案或其他控制項的所有視圖使用的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="0c7a6-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0c7a6-125">備註</span><span class="sxs-lookup"><span data-stu-id="0c7a6-125">Remarks</span></span>

<span data-ttu-id="0c7a6-126">提供給這個控制項的名稱可以在下列元素中參考：</span><span class="sxs-lookup"><span data-stu-id="0c7a6-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="0c7a6-127">CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0c7a6-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="0c7a6-128">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0c7a6-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="0c7a6-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c7a6-129">See Also</span></span>

[<span data-ttu-id="0c7a6-130">設定的控制項元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0c7a6-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="0c7a6-131">設定之控制項的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0c7a6-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="0c7a6-132">CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0c7a6-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="0c7a6-133">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0c7a6-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="0c7a6-134">設定之控制項的控制項的名稱元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0c7a6-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="0c7a6-135">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="0c7a6-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
