---
title: ExpressionBinding 之控制項的 CustomControlName 元素，用於設定 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 690b6ae01b8116b72fbd00aef574feda1fd737b0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786028"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="6d13e-102">設定之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="6d13e-102">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="6d13e-103">指定通用控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="6d13e-103">Specifies the name of a common control.</span></span> <span data-ttu-id="6d13e-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="6d13e-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="6d13e-105">Configuration 元素 (格式) Controls 設定的控制項元素 (格式設定的控制項) 控制項專案 (格式) 設定 (格式的 CustomControl 的 CustomEntries 元素) CustomEntry 元素如需設定 (格式的控制項的 CustomControl) CustomItem 元素用於 CustomEntry 的 configuration ExpressionBinding 元素) CustomItem 的 CustomControlName 元素設定 (格式的控制項)  (</span><span class="sxs-lookup"><span data-stu-id="6d13e-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6d13e-106">語法</span><span class="sxs-lookup"><span data-stu-id="6d13e-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6d13e-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6d13e-107">Attributes and Elements</span></span>

<span data-ttu-id="6d13e-108">下列各節說明屬性、子專案和元素的父元素 `CustomControlName` 。</span><span class="sxs-lookup"><span data-stu-id="6d13e-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6d13e-109">屬性</span><span class="sxs-lookup"><span data-stu-id="6d13e-109">Attributes</span></span>

<span data-ttu-id="6d13e-110">無。</span><span class="sxs-lookup"><span data-stu-id="6d13e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6d13e-111">子元素</span><span class="sxs-lookup"><span data-stu-id="6d13e-111">Child Elements</span></span>

<span data-ttu-id="6d13e-112">無。</span><span class="sxs-lookup"><span data-stu-id="6d13e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6d13e-113">父項目</span><span class="sxs-lookup"><span data-stu-id="6d13e-113">Parent Elements</span></span>

|<span data-ttu-id="6d13e-114">元素</span><span class="sxs-lookup"><span data-stu-id="6d13e-114">Element</span></span>|<span data-ttu-id="6d13e-115">描述</span><span class="sxs-lookup"><span data-stu-id="6d13e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6d13e-116">設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="6d13e-116">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="6d13e-117">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="6d13e-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6d13e-118">文字值</span><span class="sxs-lookup"><span data-stu-id="6d13e-118">Text Value</span></span>

<span data-ttu-id="6d13e-119">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="6d13e-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="6d13e-120">備註</span><span class="sxs-lookup"><span data-stu-id="6d13e-120">Remarks</span></span>

<span data-ttu-id="6d13e-121">您可以建立可供格式化檔案的所有視圖使用的通用控制項，而且可以建立可供特定視圖使用的 view 控制項。</span><span class="sxs-lookup"><span data-stu-id="6d13e-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="6d13e-122">下列元素會指定這些控制項的名稱：</span><span class="sxs-lookup"><span data-stu-id="6d13e-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="6d13e-123">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="6d13e-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="6d13e-124">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="6d13e-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="6d13e-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d13e-125">See Also</span></span>

[<span data-ttu-id="6d13e-126">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="6d13e-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="6d13e-127">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="6d13e-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="6d13e-128">設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="6d13e-128">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="6d13e-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="6d13e-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
