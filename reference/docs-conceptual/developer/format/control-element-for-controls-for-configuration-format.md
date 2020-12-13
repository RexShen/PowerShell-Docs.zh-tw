---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的控制項元素 (格式)
description: 設定之控制項的控制項元素 (格式)
ms.openlocfilehash: 43424de025cb89d81533e973abd7c39c09533747
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655653"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="51b4c-103">設定之控制項的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="51b4c-103">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="51b4c-104">定義通用控制項，可供格式化檔案的所有視圖和用來參考控制項的名稱使用。</span><span class="sxs-lookup"><span data-stu-id="51b4c-104">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="51b4c-105">Configuration 元素 (格式) 控制項的設定元素 (格式) 控制項的設定 (格式的控制項元素) </span><span class="sxs-lookup"><span data-stu-id="51b4c-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="51b4c-106">語法</span><span class="sxs-lookup"><span data-stu-id="51b4c-106">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="51b4c-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="51b4c-107">Attributes and Elements</span></span>

<span data-ttu-id="51b4c-108">下列各節描述專案的屬性、子項目和父項目 `Control` 。</span><span class="sxs-lookup"><span data-stu-id="51b4c-108">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="51b4c-109">您必須只指定每個子專案的其中一個。</span><span class="sxs-lookup"><span data-stu-id="51b4c-109">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="51b4c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="51b4c-110">Attributes</span></span>

<span data-ttu-id="51b4c-111">無。</span><span class="sxs-lookup"><span data-stu-id="51b4c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="51b4c-112">子元素</span><span class="sxs-lookup"><span data-stu-id="51b4c-112">Child Elements</span></span>

|<span data-ttu-id="51b4c-113">元素</span><span class="sxs-lookup"><span data-stu-id="51b4c-113">Element</span></span>|<span data-ttu-id="51b4c-114">描述</span><span class="sxs-lookup"><span data-stu-id="51b4c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="51b4c-115">設定之控制項的控制項 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="51b4c-115">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="51b4c-116">必要元素。</span><span class="sxs-lookup"><span data-stu-id="51b4c-116">Required element.</span></span><br /><br /> <span data-ttu-id="51b4c-117">定義控制項。</span><span class="sxs-lookup"><span data-stu-id="51b4c-117">Defines the control.</span></span>|
|[<span data-ttu-id="51b4c-118">Configuration (格式的控制項名稱元素) </span><span class="sxs-lookup"><span data-stu-id="51b4c-118">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="51b4c-119">必要元素。</span><span class="sxs-lookup"><span data-stu-id="51b4c-119">Required element.</span></span><br /><br /> <span data-ttu-id="51b4c-120">指定用來參考控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="51b4c-120">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="51b4c-121">父項目</span><span class="sxs-lookup"><span data-stu-id="51b4c-121">Parent Elements</span></span>

|<span data-ttu-id="51b4c-122">元素</span><span class="sxs-lookup"><span data-stu-id="51b4c-122">Element</span></span>|<span data-ttu-id="51b4c-123">描述</span><span class="sxs-lookup"><span data-stu-id="51b4c-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="51b4c-124">Configuration (格式的 Controls 元素) </span><span class="sxs-lookup"><span data-stu-id="51b4c-124">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="51b4c-125">定義可供格式化檔案的所有視圖或其他控制項使用的通用控制項。</span><span class="sxs-lookup"><span data-stu-id="51b4c-125">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="51b4c-126">備註</span><span class="sxs-lookup"><span data-stu-id="51b4c-126">Remarks</span></span>

<span data-ttu-id="51b4c-127">您可以在下列專案中參考提供給這個控制項的名稱：</span><span class="sxs-lookup"><span data-stu-id="51b4c-127">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="51b4c-128">CustomItem (格式的 ExpressionBinding 元素) </span><span class="sxs-lookup"><span data-stu-id="51b4c-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="51b4c-129">View (格式的 GroupBy 元素) </span><span class="sxs-lookup"><span data-stu-id="51b4c-129">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="51b4c-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51b4c-130">See Also</span></span>

[<span data-ttu-id="51b4c-131">Configuration (格式的 Controls 元素) </span><span class="sxs-lookup"><span data-stu-id="51b4c-131">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="51b4c-132">CustomControl 元素，可控制設定 (格式) </span><span class="sxs-lookup"><span data-stu-id="51b4c-132">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="51b4c-133">CustomItem (格式的 ExpressionBinding 元素) </span><span class="sxs-lookup"><span data-stu-id="51b4c-133">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="51b4c-134">View (格式的 GroupBy 元素) </span><span class="sxs-lookup"><span data-stu-id="51b4c-134">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="51b4c-135">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="51b4c-135">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="51b4c-136">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="51b4c-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
