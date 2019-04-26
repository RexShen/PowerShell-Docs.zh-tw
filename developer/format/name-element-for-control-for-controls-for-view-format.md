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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065088"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="42f52-102">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="42f52-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="42f52-103">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="42f52-103">Specifies the name of the control.</span></span>

<span data-ttu-id="42f52-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） 名稱的項目控制項的檢視 （格式）</span><span class="sxs-lookup"><span data-stu-id="42f52-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="42f52-105">語法</span><span class="sxs-lookup"><span data-stu-id="42f52-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="42f52-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="42f52-106">Attributes and Elements</span></span>

<span data-ttu-id="42f52-107">下列各節說明屬性、 子項目和父項目`Name`項目。</span><span class="sxs-lookup"><span data-stu-id="42f52-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="42f52-108">屬性</span><span class="sxs-lookup"><span data-stu-id="42f52-108">Attributes</span></span>

<span data-ttu-id="42f52-109">無。</span><span class="sxs-lookup"><span data-stu-id="42f52-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="42f52-110">子元素</span><span class="sxs-lookup"><span data-stu-id="42f52-110">Child Elements</span></span>

<span data-ttu-id="42f52-111">無。</span><span class="sxs-lookup"><span data-stu-id="42f52-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="42f52-112">父項目</span><span class="sxs-lookup"><span data-stu-id="42f52-112">Parent Elements</span></span>

|<span data-ttu-id="42f52-113">項目</span><span class="sxs-lookup"><span data-stu-id="42f52-113">Element</span></span>|<span data-ttu-id="42f52-114">描述</span><span class="sxs-lookup"><span data-stu-id="42f52-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="42f52-115">用於檢視 （格式） 的控制項的控制項項目</span><span class="sxs-lookup"><span data-stu-id="42f52-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="42f52-116">定義可供檢視和名稱，用來參考控制項的控制項。</span><span class="sxs-lookup"><span data-stu-id="42f52-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="42f52-117">文字值</span><span class="sxs-lookup"><span data-stu-id="42f52-117">Text Value</span></span>

<span data-ttu-id="42f52-118">指定用來參考控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="42f52-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="42f52-119">備註</span><span class="sxs-lookup"><span data-stu-id="42f52-119">Remarks</span></span>

<span data-ttu-id="42f52-120">在這裡指定的名稱可以用於下列項目，來參考這個控制項。</span><span class="sxs-lookup"><span data-stu-id="42f52-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="42f52-121">在建立資料表、 清單、 寬或自訂的控制項檢視時，可以指定的控制項，由下列項目：[檢視 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="42f52-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="42f52-122">當建立另一個控制項，可供檢視時，此控制項可以指定下列項目：[ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="42f52-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="42f52-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42f52-123">See Also</span></span>

[<span data-ttu-id="42f52-124">檢視 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="42f52-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="42f52-125">ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="42f52-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="42f52-126">用於檢視 （格式） 的控制項的控制項項目</span><span class="sxs-lookup"><span data-stu-id="42f52-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="42f52-127">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="42f52-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
