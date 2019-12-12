---
title: View 之控制項的控制項的名稱元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365097"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="a6a87-102">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a6a87-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="a6a87-103">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="a6a87-103">Specifies the name of the control.</span></span>

<span data-ttu-id="a6a87-104">設定專案（格式） ViewDefinitions 元素（格式） View 元素（格式）控制項元素（格式）控制項專案（適用于 view 的 View （Format） Name 元素）（格式）</span><span class="sxs-lookup"><span data-stu-id="a6a87-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a6a87-105">語法</span><span class="sxs-lookup"><span data-stu-id="a6a87-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a6a87-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="a6a87-106">Attributes and Elements</span></span>

<span data-ttu-id="a6a87-107">下列各節說明屬性、子專案，以及 `Name` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="a6a87-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a6a87-108">屬性</span><span class="sxs-lookup"><span data-stu-id="a6a87-108">Attributes</span></span>

<span data-ttu-id="a6a87-109">無。</span><span class="sxs-lookup"><span data-stu-id="a6a87-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a6a87-110">子元素</span><span class="sxs-lookup"><span data-stu-id="a6a87-110">Child Elements</span></span>

<span data-ttu-id="a6a87-111">無。</span><span class="sxs-lookup"><span data-stu-id="a6a87-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a6a87-112">父元素</span><span class="sxs-lookup"><span data-stu-id="a6a87-112">Parent Elements</span></span>

|<span data-ttu-id="a6a87-113">元素</span><span class="sxs-lookup"><span data-stu-id="a6a87-113">Element</span></span>|<span data-ttu-id="a6a87-114">描述</span><span class="sxs-lookup"><span data-stu-id="a6a87-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a6a87-115">View 控制項的控制項元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6a87-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="a6a87-116">定義可供視圖使用的控制項，以及用來參考控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="a6a87-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a6a87-117">文字值</span><span class="sxs-lookup"><span data-stu-id="a6a87-117">Text Value</span></span>

<span data-ttu-id="a6a87-118">指定用來參考控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="a6a87-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="a6a87-119">備註</span><span class="sxs-lookup"><span data-stu-id="a6a87-119">Remarks</span></span>

<span data-ttu-id="a6a87-120">這裡指定的名稱可用於下列專案，以參考此控制項。</span><span class="sxs-lookup"><span data-stu-id="a6a87-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="a6a87-121">建立 [資料表]、[清單]、[寬] 或 [自訂] 控制項時，控制項可以由下列元素指定： [ [GroupBy] 元素（格式）](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="a6a87-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="a6a87-122">建立可供視圖使用的另一個控制項時，這個控制項可以由下列元素指定： [ExpressionBinding 元素用於 CustomItem 的控制項（格式）](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="a6a87-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="a6a87-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6a87-123">See Also</span></span>

[<span data-ttu-id="a6a87-124">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6a87-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="a6a87-125">View 之控制項的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6a87-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="a6a87-126">View 控制項的控制項元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6a87-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="a6a87-127">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="a6a87-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
