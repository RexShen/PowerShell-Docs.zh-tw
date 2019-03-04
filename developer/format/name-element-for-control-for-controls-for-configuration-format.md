---
title: 控制項名稱項目控制項的組態 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860084"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="d8412-102">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d8412-102">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="d8412-103">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="d8412-103">Specifies the name of the control.</span></span> <span data-ttu-id="d8412-104">定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="d8412-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="d8412-105">組態 （格式） 的組態 （格式） 名稱的項目組態 （格式） 的控制項的控制項的控制項的控制項項目的組態項目 （格式） 的控制項項目</span><span class="sxs-lookup"><span data-stu-id="d8412-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d8412-106">語法</span><span class="sxs-lookup"><span data-stu-id="d8412-106">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d8412-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="d8412-107">Attributes and Elements</span></span>

<span data-ttu-id="d8412-108">下列各節說明屬性、 子項目和父項目`Name`項目。</span><span class="sxs-lookup"><span data-stu-id="d8412-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d8412-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d8412-109">Attributes</span></span>

<span data-ttu-id="d8412-110">無。</span><span class="sxs-lookup"><span data-stu-id="d8412-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d8412-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d8412-111">Child Elements</span></span>

<span data-ttu-id="d8412-112">無。</span><span class="sxs-lookup"><span data-stu-id="d8412-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d8412-113">父元素</span><span class="sxs-lookup"><span data-stu-id="d8412-113">Parent Elements</span></span>

|<span data-ttu-id="d8412-114">元素</span><span class="sxs-lookup"><span data-stu-id="d8412-114">Element</span></span>|<span data-ttu-id="d8412-115">描述</span><span class="sxs-lookup"><span data-stu-id="d8412-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d8412-116">組態 （格式） 的控制項的控制項項目</span><span class="sxs-lookup"><span data-stu-id="d8412-116">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="d8412-117">定義可供的格式化檔案以及用來參考的控制項名稱的所有檢視通用控制項。</span><span class="sxs-lookup"><span data-stu-id="d8412-117">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d8412-118">文字值</span><span class="sxs-lookup"><span data-stu-id="d8412-118">Text Value</span></span>

<span data-ttu-id="d8412-119">指定用來參考這個控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="d8412-119">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="d8412-120">備註</span><span class="sxs-lookup"><span data-stu-id="d8412-120">Remarks</span></span>

<span data-ttu-id="d8412-121">在這裡指定的名稱可以用於下列項目，來參考這個控制項。</span><span class="sxs-lookup"><span data-stu-id="d8412-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="d8412-122">在建立資料表、 清單、 寬或自訂的控制項檢視時，可以指定的控制項，由下列項目：[檢視 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="d8412-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="d8412-123">當建立另一個常見的控制項，此控制項可以指定由下列項目：[ExpressionBinding CustomItem 組態 （格式） 的控制項的項目](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="d8412-123">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="d8412-124">當建立控制項，可供檢視時，這個控制項可以指定下列項目：[ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="d8412-124">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="d8412-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8412-125">See Also</span></span>

[<span data-ttu-id="d8412-126">組態 （格式） 的控制項的控制項項目</span><span class="sxs-lookup"><span data-stu-id="d8412-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="d8412-127">ExpressionBinding CustomItem 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="d8412-127">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="d8412-128">ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="d8412-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="d8412-129">檢視 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="d8412-129">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="d8412-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="d8412-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
