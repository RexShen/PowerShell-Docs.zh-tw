---
title: View (Format) 的控制項之 ExpressionBinding 的 CustomControlName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 871c6afd89db9360ea5012191b08863a9441f899
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786011"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="b0c64-102">檢視之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b0c64-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="b0c64-103">指定通用控制項或 view 控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="b0c64-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="b0c64-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="b0c64-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b0c64-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 CustomControl， (格式控制項的控制項) CustomEntries 元素用於 view (針對 (格式的控制項，) CustomEntry 元素格式) CustomItem 專案的 CustomEntry for view (Format) ExpressionBinding 元素 for view (format) CustomItem 元素 for 控制項 for view (format) CustomControlName 專案</span><span class="sxs-lookup"><span data-stu-id="b0c64-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b0c64-106">語法</span><span class="sxs-lookup"><span data-stu-id="b0c64-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b0c64-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b0c64-107">Attributes and Elements</span></span>

<span data-ttu-id="b0c64-108">下列各節說明屬性、子專案和元素的父元素 `CustomControlName` 。</span><span class="sxs-lookup"><span data-stu-id="b0c64-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b0c64-109">屬性</span><span class="sxs-lookup"><span data-stu-id="b0c64-109">Attributes</span></span>

<span data-ttu-id="b0c64-110">無。</span><span class="sxs-lookup"><span data-stu-id="b0c64-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b0c64-111">子元素</span><span class="sxs-lookup"><span data-stu-id="b0c64-111">Child Elements</span></span>

<span data-ttu-id="b0c64-112">無。</span><span class="sxs-lookup"><span data-stu-id="b0c64-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b0c64-113">父項目</span><span class="sxs-lookup"><span data-stu-id="b0c64-113">Parent Elements</span></span>

|<span data-ttu-id="b0c64-114">元素</span><span class="sxs-lookup"><span data-stu-id="b0c64-114">Element</span></span>|<span data-ttu-id="b0c64-115">描述</span><span class="sxs-lookup"><span data-stu-id="b0c64-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b0c64-116">檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b0c64-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="b0c64-117">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="b0c64-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b0c64-118">文字值</span><span class="sxs-lookup"><span data-stu-id="b0c64-118">Text Value</span></span>

<span data-ttu-id="b0c64-119">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="b0c64-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="b0c64-120">備註</span><span class="sxs-lookup"><span data-stu-id="b0c64-120">Remarks</span></span>

<span data-ttu-id="b0c64-121">您可以建立可供格式化檔案的所有視圖使用的通用控制項，而且可以建立可供特定視圖使用的 view 控制項。</span><span class="sxs-lookup"><span data-stu-id="b0c64-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="b0c64-122">下列元素會指定這些控制項的名稱：</span><span class="sxs-lookup"><span data-stu-id="b0c64-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="b0c64-123">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b0c64-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="b0c64-124">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b0c64-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="b0c64-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0c64-125">See Also</span></span>

[<span data-ttu-id="b0c64-126">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b0c64-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="b0c64-127">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b0c64-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="b0c64-128">檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b0c64-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="b0c64-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="b0c64-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
