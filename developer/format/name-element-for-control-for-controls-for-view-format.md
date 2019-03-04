---
title: 控制項名稱項目控制項的檢視 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862384"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="97e51-102">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="97e51-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="97e51-103">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="97e51-103">Specifies the name of the control.</span></span>

<span data-ttu-id="97e51-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） 名稱的項目控制項的檢視 （格式）</span><span class="sxs-lookup"><span data-stu-id="97e51-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="97e51-105">語法</span><span class="sxs-lookup"><span data-stu-id="97e51-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="97e51-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="97e51-106">Attributes and Elements</span></span>

<span data-ttu-id="97e51-107">下列各節說明屬性、 子項目和父項目`Name`項目。</span><span class="sxs-lookup"><span data-stu-id="97e51-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="97e51-108">屬性</span><span class="sxs-lookup"><span data-stu-id="97e51-108">Attributes</span></span>

<span data-ttu-id="97e51-109">無。</span><span class="sxs-lookup"><span data-stu-id="97e51-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="97e51-110">子元素</span><span class="sxs-lookup"><span data-stu-id="97e51-110">Child Elements</span></span>

<span data-ttu-id="97e51-111">無。</span><span class="sxs-lookup"><span data-stu-id="97e51-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="97e51-112">父元素</span><span class="sxs-lookup"><span data-stu-id="97e51-112">Parent Elements</span></span>

|<span data-ttu-id="97e51-113">元素</span><span class="sxs-lookup"><span data-stu-id="97e51-113">Element</span></span>|<span data-ttu-id="97e51-114">描述</span><span class="sxs-lookup"><span data-stu-id="97e51-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="97e51-115">用於檢視 （格式） 的控制項的控制項項目</span><span class="sxs-lookup"><span data-stu-id="97e51-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="97e51-116">定義可供檢視和名稱，用來參考控制項的控制項。</span><span class="sxs-lookup"><span data-stu-id="97e51-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="97e51-117">文字值</span><span class="sxs-lookup"><span data-stu-id="97e51-117">Text Value</span></span>

<span data-ttu-id="97e51-118">指定用來參考控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="97e51-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="97e51-119">備註</span><span class="sxs-lookup"><span data-stu-id="97e51-119">Remarks</span></span>

<span data-ttu-id="97e51-120">在這裡指定的名稱可以用於下列項目，來參考這個控制項。</span><span class="sxs-lookup"><span data-stu-id="97e51-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="97e51-121">在建立資料表、 清單、 寬或自訂的控制項檢視時，可以指定的控制項，由下列項目：[檢視 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="97e51-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="97e51-122">當建立另一個控制項，可供檢視時，此控制項可以指定下列項目：[ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="97e51-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="97e51-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97e51-123">See Also</span></span>

[<span data-ttu-id="97e51-124">檢視 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="97e51-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="97e51-125">ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="97e51-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="97e51-126">用於檢視 （格式） 的控制項的控制項項目</span><span class="sxs-lookup"><span data-stu-id="97e51-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="97e51-127">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="97e51-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
