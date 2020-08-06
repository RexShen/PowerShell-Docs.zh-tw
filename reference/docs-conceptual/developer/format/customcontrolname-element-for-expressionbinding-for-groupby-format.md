---
title: 適用于 ExpressionBinding 之 GroupBy (格式的 CustomControlName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 06e612b25accf81467108ca48500943153efd575
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785994"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="d258b-102">GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d258b-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="d258b-103">指定通用控制項或 view 控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="d258b-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="d258b-104">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="d258b-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="d258b-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) GroupBy 元素以取得 (格式) CustomEntries 專案（適用于 groupby (format）) CustomEntry 元素（適用于 CustomControl 的 groupby (格式) CustomItem 元素，適用于 groupby (格式的 CustomEntry) ExpressionBinding 專案 (]</span><span class="sxs-lookup"><span data-stu-id="d258b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d258b-106">語法</span><span class="sxs-lookup"><span data-stu-id="d258b-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d258b-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d258b-107">Attributes and Elements</span></span>

<span data-ttu-id="d258b-108">下列各節說明屬性、子專案和元素的父元素 `CustomControlName` 。</span><span class="sxs-lookup"><span data-stu-id="d258b-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d258b-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d258b-109">Attributes</span></span>

<span data-ttu-id="d258b-110">無。</span><span class="sxs-lookup"><span data-stu-id="d258b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d258b-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d258b-111">Child Elements</span></span>

<span data-ttu-id="d258b-112">無。</span><span class="sxs-lookup"><span data-stu-id="d258b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d258b-113">父項目</span><span class="sxs-lookup"><span data-stu-id="d258b-113">Parent Elements</span></span>

|<span data-ttu-id="d258b-114">元素</span><span class="sxs-lookup"><span data-stu-id="d258b-114">Element</span></span>|<span data-ttu-id="d258b-115">描述</span><span class="sxs-lookup"><span data-stu-id="d258b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d258b-116">GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d258b-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="d258b-117">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="d258b-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d258b-118">文字值</span><span class="sxs-lookup"><span data-stu-id="d258b-118">Text Value</span></span>

<span data-ttu-id="d258b-119">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="d258b-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="d258b-120">備註</span><span class="sxs-lookup"><span data-stu-id="d258b-120">Remarks</span></span>

<span data-ttu-id="d258b-121">您可以建立可供格式化檔案的所有視圖使用的通用控制項，而且可以建立可供特定視圖使用的 view 控制項。</span><span class="sxs-lookup"><span data-stu-id="d258b-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="d258b-122">下列元素會指定這些控制項的名稱：</span><span class="sxs-lookup"><span data-stu-id="d258b-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="d258b-123">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d258b-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="d258b-124">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d258b-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="d258b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d258b-125">See Also</span></span>

[<span data-ttu-id="d258b-126">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d258b-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="d258b-127">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d258b-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="d258b-128">GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d258b-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="d258b-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="d258b-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
