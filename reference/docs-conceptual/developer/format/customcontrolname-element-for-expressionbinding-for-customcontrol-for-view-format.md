---
title: CustomControl for View (格式) 的 ExpressionBinding 的 CustomControlName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6f1ffca045b7efcecb4dce4e788a8c508fa6ef08
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783750"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="165d9-102">檢視之 CustomControl 的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="165d9-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="165d9-103">指定通用控制項或 view 控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="165d9-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="165d9-104">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="165d9-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="165d9-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) CustomControl 元素 for view (format) CustomControl for view (format) CustomEntry 元素，CustomEntries for view (format) CustomItem 專案 for CustomEntry (Format) ExpressionBinding 元素 for CustomItem 的 Expression Binding (格式) </span><span class="sxs-lookup"><span data-stu-id="165d9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="165d9-106">語法</span><span class="sxs-lookup"><span data-stu-id="165d9-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="165d9-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="165d9-107">Attributes and Elements</span></span>

<span data-ttu-id="165d9-108">下列各節說明屬性、子專案和元素的父元素 `CustomControlName` 。</span><span class="sxs-lookup"><span data-stu-id="165d9-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="165d9-109">屬性</span><span class="sxs-lookup"><span data-stu-id="165d9-109">Attributes</span></span>

<span data-ttu-id="165d9-110">無。</span><span class="sxs-lookup"><span data-stu-id="165d9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="165d9-111">子元素</span><span class="sxs-lookup"><span data-stu-id="165d9-111">Child Elements</span></span>

<span data-ttu-id="165d9-112">無。</span><span class="sxs-lookup"><span data-stu-id="165d9-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="165d9-113">父項目</span><span class="sxs-lookup"><span data-stu-id="165d9-113">Parent Elements</span></span>

|<span data-ttu-id="165d9-114">元素</span><span class="sxs-lookup"><span data-stu-id="165d9-114">Element</span></span>|<span data-ttu-id="165d9-115">描述</span><span class="sxs-lookup"><span data-stu-id="165d9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="165d9-116">CustomItem (格式的 ExpressionBinding 元素) </span><span class="sxs-lookup"><span data-stu-id="165d9-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="165d9-117">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="165d9-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="165d9-118">文字值</span><span class="sxs-lookup"><span data-stu-id="165d9-118">Text Value</span></span>

<span data-ttu-id="165d9-119">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="165d9-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="165d9-120">備註</span><span class="sxs-lookup"><span data-stu-id="165d9-120">Remarks</span></span>

<span data-ttu-id="165d9-121">您可以建立可供格式化檔案的所有視圖使用的通用控制項，而且可以建立可供特定視圖使用的 view 控制項。</span><span class="sxs-lookup"><span data-stu-id="165d9-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="165d9-122">這些控制項的名稱是由下列元素所指定。</span><span class="sxs-lookup"><span data-stu-id="165d9-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="165d9-123">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="165d9-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="165d9-124">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="165d9-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="165d9-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="165d9-125">See Also</span></span>

[<span data-ttu-id="165d9-126">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="165d9-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="165d9-127">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="165d9-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="165d9-128">CustomItem (格式的 ExpressionBinding 元素) </span><span class="sxs-lookup"><span data-stu-id="165d9-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="165d9-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="165d9-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
