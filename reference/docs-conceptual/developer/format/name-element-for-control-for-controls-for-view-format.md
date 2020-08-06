---
title: View (格式) 的控制項之控制項的名稱元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 109f3a40606dbe82322decf0c69d2367c75175f6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781081"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="6c455-102">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="6c455-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="6c455-103">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="6c455-103">Specifies the name of the control.</span></span>

<span data-ttu-id="6c455-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案，視圖 (格式的控制項) Name 元素 (</span><span class="sxs-lookup"><span data-stu-id="6c455-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6c455-105">語法</span><span class="sxs-lookup"><span data-stu-id="6c455-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6c455-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6c455-106">Attributes and Elements</span></span>

<span data-ttu-id="6c455-107">下列各節說明屬性、子專案和元素的父元素 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="6c455-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6c455-108">屬性</span><span class="sxs-lookup"><span data-stu-id="6c455-108">Attributes</span></span>

<span data-ttu-id="6c455-109">無。</span><span class="sxs-lookup"><span data-stu-id="6c455-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6c455-110">子元素</span><span class="sxs-lookup"><span data-stu-id="6c455-110">Child Elements</span></span>

<span data-ttu-id="6c455-111">無。</span><span class="sxs-lookup"><span data-stu-id="6c455-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6c455-112">父項目</span><span class="sxs-lookup"><span data-stu-id="6c455-112">Parent Elements</span></span>

|<span data-ttu-id="6c455-113">元素</span><span class="sxs-lookup"><span data-stu-id="6c455-113">Element</span></span>|<span data-ttu-id="6c455-114">描述</span><span class="sxs-lookup"><span data-stu-id="6c455-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6c455-115">View (格式之控制項的控制項元素) </span><span class="sxs-lookup"><span data-stu-id="6c455-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="6c455-116">定義可供視圖使用的控制項，以及用來參考控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="6c455-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6c455-117">文字值</span><span class="sxs-lookup"><span data-stu-id="6c455-117">Text Value</span></span>

<span data-ttu-id="6c455-118">指定用來參考控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="6c455-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="6c455-119">備註</span><span class="sxs-lookup"><span data-stu-id="6c455-119">Remarks</span></span>

<span data-ttu-id="6c455-120">這裡指定的名稱可用於下列專案，以參考此控制項。</span><span class="sxs-lookup"><span data-stu-id="6c455-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="6c455-121">建立 [資料表]、[清單]、[寬] 或 [自訂] 控制項時，下列專案可以指定控制項： [view (格式的 GroupBy 元素) ](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="6c455-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="6c455-122">建立可供視圖使用的另一個控制項時，這個控制項可以由下列元素指定： [CustomItem 的 ExpressionBinding 元素，用於 view (格式的控制項) ](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="6c455-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="6c455-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c455-123">See Also</span></span>

[<span data-ttu-id="6c455-124">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="6c455-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="6c455-125">檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="6c455-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="6c455-126">View (格式之控制項的控制項元素) </span><span class="sxs-lookup"><span data-stu-id="6c455-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="6c455-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="6c455-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
