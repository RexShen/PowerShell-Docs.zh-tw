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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369007"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="2850c-102">設定之控制項的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2850c-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="2850c-103">定義可供格式檔案的所有視圖使用的通用控制項，以及用來參考控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="2850c-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="2850c-104">Configuration 元素（Format）控制設定之控制項的設定（格式）控制項元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2850c-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2850c-105">語法</span><span class="sxs-lookup"><span data-stu-id="2850c-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2850c-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="2850c-106">Attributes and Elements</span></span>

<span data-ttu-id="2850c-107">下列各節說明屬性、子專案，以及 `Control` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="2850c-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="2850c-108">您必須只指定其中一個子項目。</span><span class="sxs-lookup"><span data-stu-id="2850c-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2850c-109">屬性</span><span class="sxs-lookup"><span data-stu-id="2850c-109">Attributes</span></span>

<span data-ttu-id="2850c-110">無。</span><span class="sxs-lookup"><span data-stu-id="2850c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2850c-111">子元素</span><span class="sxs-lookup"><span data-stu-id="2850c-111">Child Elements</span></span>

|<span data-ttu-id="2850c-112">元素</span><span class="sxs-lookup"><span data-stu-id="2850c-112">Element</span></span>|<span data-ttu-id="2850c-113">描述</span><span class="sxs-lookup"><span data-stu-id="2850c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2850c-114">設定之控制項控制項的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2850c-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="2850c-115">必要項目。</span><span class="sxs-lookup"><span data-stu-id="2850c-115">Required element.</span></span><br /><br /> <span data-ttu-id="2850c-116">定義控制項。</span><span class="sxs-lookup"><span data-stu-id="2850c-116">Defines the control.</span></span>|
|[<span data-ttu-id="2850c-117">設定之控制項的名稱元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2850c-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="2850c-118">必要項目。</span><span class="sxs-lookup"><span data-stu-id="2850c-118">Required element.</span></span><br /><br /> <span data-ttu-id="2850c-119">指定用來參考控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="2850c-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2850c-120">父元素</span><span class="sxs-lookup"><span data-stu-id="2850c-120">Parent Elements</span></span>

|<span data-ttu-id="2850c-121">元素</span><span class="sxs-lookup"><span data-stu-id="2850c-121">Element</span></span>|<span data-ttu-id="2850c-122">描述</span><span class="sxs-lookup"><span data-stu-id="2850c-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2850c-123">設定的控制項元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2850c-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="2850c-124">定義可供格式檔案或其他控制項的所有視圖使用的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="2850c-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2850c-125">備註</span><span class="sxs-lookup"><span data-stu-id="2850c-125">Remarks</span></span>

<span data-ttu-id="2850c-126">提供給這個控制項的名稱可以在下列元素中參考：</span><span class="sxs-lookup"><span data-stu-id="2850c-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="2850c-127">CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2850c-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="2850c-128">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2850c-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="2850c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2850c-129">See Also</span></span>

[<span data-ttu-id="2850c-130">設定的控制項元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2850c-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="2850c-131">設定之控制項的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2850c-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="2850c-132">CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2850c-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="2850c-133">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2850c-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="2850c-134">設定之控制項的控制項的名稱元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2850c-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="2850c-135">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="2850c-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
