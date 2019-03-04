---
title: 用於檢視 （格式） 的控制項 ExpressionBinding CustomControlName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855594"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="a1a1e-102">檢視之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a1a1e-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="a1a1e-103">指定通用控制項的檢視控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="a1a1e-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="a1a1e-104">定義可供檢視的控制項時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="a1a1e-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="a1a1e-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目CustomControl CustomEntries CustomEntry CustomItem 用於檢視 （格式） CustomControlName 的控制項的檢視 （格式） ExpressionBinding 元素的控制項的檢視 （格式） CustomItem 元素的控制項的檢視 （格式） CustomEntry 元素用於檢視 （格式） 的控制項 ExpressionBindine 的項目</span><span class="sxs-lookup"><span data-stu-id="a1a1e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a1a1e-106">語法</span><span class="sxs-lookup"><span data-stu-id="a1a1e-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a1a1e-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="a1a1e-107">Attributes and Elements</span></span>

<span data-ttu-id="a1a1e-108">下列各節說明屬性、 子項目和父項目`CustomControlName`項目。</span><span class="sxs-lookup"><span data-stu-id="a1a1e-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a1a1e-109">屬性</span><span class="sxs-lookup"><span data-stu-id="a1a1e-109">Attributes</span></span>

<span data-ttu-id="a1a1e-110">無。</span><span class="sxs-lookup"><span data-stu-id="a1a1e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a1a1e-111">子元素</span><span class="sxs-lookup"><span data-stu-id="a1a1e-111">Child Elements</span></span>

<span data-ttu-id="a1a1e-112">無。</span><span class="sxs-lookup"><span data-stu-id="a1a1e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a1a1e-113">父元素</span><span class="sxs-lookup"><span data-stu-id="a1a1e-113">Parent Elements</span></span>

|<span data-ttu-id="a1a1e-114">元素</span><span class="sxs-lookup"><span data-stu-id="a1a1e-114">Element</span></span>|<span data-ttu-id="a1a1e-115">描述</span><span class="sxs-lookup"><span data-stu-id="a1a1e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a1a1e-116">ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="a1a1e-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="a1a1e-117">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="a1a1e-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a1a1e-118">文字值</span><span class="sxs-lookup"><span data-stu-id="a1a1e-118">Text Value</span></span>

<span data-ttu-id="a1a1e-119">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="a1a1e-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="a1a1e-120">備註</span><span class="sxs-lookup"><span data-stu-id="a1a1e-120">Remarks</span></span>

<span data-ttu-id="a1a1e-121">您可以建立可供所有的格式化檔案，檢視的通用控制項，而且您可以建立可供特定檢視的檢視控制項。</span><span class="sxs-lookup"><span data-stu-id="a1a1e-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="a1a1e-122">下列項目會指定這些控制項的名稱：</span><span class="sxs-lookup"><span data-stu-id="a1a1e-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="a1a1e-123">組態 （格式） 的控制項的控制項的 name 元素</span><span class="sxs-lookup"><span data-stu-id="a1a1e-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="a1a1e-124">用於檢視 （格式） 的控制項的控制項的 name 元素</span><span class="sxs-lookup"><span data-stu-id="a1a1e-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="a1a1e-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1a1e-125">See Also</span></span>

[<span data-ttu-id="a1a1e-126">組態 （格式） 的控制項的控制項的 name 元素</span><span class="sxs-lookup"><span data-stu-id="a1a1e-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="a1a1e-127">用於檢視 （格式） 的控制項的控制項的 name 元素</span><span class="sxs-lookup"><span data-stu-id="a1a1e-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="a1a1e-128">ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="a1a1e-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="a1a1e-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="a1a1e-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
