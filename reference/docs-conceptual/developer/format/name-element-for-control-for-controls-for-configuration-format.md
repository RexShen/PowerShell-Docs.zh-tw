---
title: 設定 (格式) 的控制項之控制項的名稱元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3d45ba98b909ebee18e01d2b6985a48906ce39d9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783529"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="4f0b3-102">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4f0b3-102">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="4f0b3-103">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="4f0b3-103">Specifies the name of the control.</span></span> <span data-ttu-id="4f0b3-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="4f0b3-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="4f0b3-105">Configuration 元素 (格式) Controls 設定的控制項元素 (格式設定的控制項) 控制項專案 (格式) Name 元素用於設定 (格式的控制項) </span><span class="sxs-lookup"><span data-stu-id="4f0b3-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4f0b3-106">語法</span><span class="sxs-lookup"><span data-stu-id="4f0b3-106">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="4f0b3-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4f0b3-107">Attributes and Elements</span></span>

<span data-ttu-id="4f0b3-108">下列各節說明屬性、子專案和元素的父元素 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="4f0b3-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4f0b3-109">屬性</span><span class="sxs-lookup"><span data-stu-id="4f0b3-109">Attributes</span></span>

<span data-ttu-id="4f0b3-110">無。</span><span class="sxs-lookup"><span data-stu-id="4f0b3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4f0b3-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4f0b3-111">Child Elements</span></span>

<span data-ttu-id="4f0b3-112">無。</span><span class="sxs-lookup"><span data-stu-id="4f0b3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4f0b3-113">父項目</span><span class="sxs-lookup"><span data-stu-id="4f0b3-113">Parent Elements</span></span>

|<span data-ttu-id="4f0b3-114">元素</span><span class="sxs-lookup"><span data-stu-id="4f0b3-114">Element</span></span>|<span data-ttu-id="4f0b3-115">描述</span><span class="sxs-lookup"><span data-stu-id="4f0b3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4f0b3-116">設定之控制項的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4f0b3-116">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="4f0b3-117">定義可供格式檔案的所有視圖使用的通用控制項，以及用來參考控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="4f0b3-117">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4f0b3-118">文字值</span><span class="sxs-lookup"><span data-stu-id="4f0b3-118">Text Value</span></span>

<span data-ttu-id="4f0b3-119">指定用來參考此控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="4f0b3-119">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="4f0b3-120">備註</span><span class="sxs-lookup"><span data-stu-id="4f0b3-120">Remarks</span></span>

<span data-ttu-id="4f0b3-121">這裡指定的名稱可用於下列專案，以參考此控制項。</span><span class="sxs-lookup"><span data-stu-id="4f0b3-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="4f0b3-122">建立 [資料表]、[清單]、[寬] 或 [自訂] 控制項時，下列專案可以指定控制項： [view (格式的 GroupBy 元素) ](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="4f0b3-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="4f0b3-123">建立另一個通用控制項時，這個控制項可以由下列元素指定： [CustomItem 的 ExpressionBinding 元素，用於設定 (格式的控制項) ](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="4f0b3-123">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="4f0b3-124">建立可供視圖使用的控制項時，這個控制項可以由下列元素指定： [CustomItem 的 ExpressionBinding 元素，用於 view (格式的控制項) ](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="4f0b3-124">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="4f0b3-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f0b3-125">See Also</span></span>

[<span data-ttu-id="4f0b3-126">設定之控制項的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4f0b3-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="4f0b3-127">設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4f0b3-127">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="4f0b3-128">檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4f0b3-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="4f0b3-129">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4f0b3-129">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="4f0b3-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="4f0b3-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
