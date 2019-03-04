---
title: CustomControlName CustomControl 檢視 （格式） 的 ExpressionBinding 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860434"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="cc107-102">檢視之 CustomControl 的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="cc107-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="cc107-103">指定通用控制項的檢視控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="cc107-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="cc107-104">定義自訂控制項的檢視時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="cc107-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="cc107-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目進行檢視 （格式） 的檢視 （格式） CustomItem CustomEntries CustomEntry 元素 CustomControl 的檢視 （格式） CustomEntries 項目CustomEntry CustomItem （格式） CustomControlName 元素 CustomItem （格式） 的運算式繫結的檢視 （格式） ExpressionBinding 項目的項目</span><span class="sxs-lookup"><span data-stu-id="cc107-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cc107-106">語法</span><span class="sxs-lookup"><span data-stu-id="cc107-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cc107-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="cc107-107">Attributes and Elements</span></span>

<span data-ttu-id="cc107-108">下列各節說明屬性、 子項目和父項目`CustomControlName`項目。</span><span class="sxs-lookup"><span data-stu-id="cc107-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cc107-109">屬性</span><span class="sxs-lookup"><span data-stu-id="cc107-109">Attributes</span></span>

<span data-ttu-id="cc107-110">無。</span><span class="sxs-lookup"><span data-stu-id="cc107-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cc107-111">子元素</span><span class="sxs-lookup"><span data-stu-id="cc107-111">Child Elements</span></span>

<span data-ttu-id="cc107-112">無。</span><span class="sxs-lookup"><span data-stu-id="cc107-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cc107-113">父元素</span><span class="sxs-lookup"><span data-stu-id="cc107-113">Parent Elements</span></span>

|<span data-ttu-id="cc107-114">元素</span><span class="sxs-lookup"><span data-stu-id="cc107-114">Element</span></span>|<span data-ttu-id="cc107-115">描述</span><span class="sxs-lookup"><span data-stu-id="cc107-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cc107-116">ExpressionBinding CustomItem （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="cc107-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="cc107-117">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="cc107-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cc107-118">文字值</span><span class="sxs-lookup"><span data-stu-id="cc107-118">Text Value</span></span>

<span data-ttu-id="cc107-119">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="cc107-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="cc107-120">備註</span><span class="sxs-lookup"><span data-stu-id="cc107-120">Remarks</span></span>

<span data-ttu-id="cc107-121">您可以建立可供的格式化檔案的所有檢視通用控制項，而且您可以建立可都供特定檢視的檢視控制項。</span><span class="sxs-lookup"><span data-stu-id="cc107-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="cc107-122">這些控制項的名稱是由下列項目指定。</span><span class="sxs-lookup"><span data-stu-id="cc107-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="cc107-123">組態 （格式） 的控制項的控制項的 name 元素</span><span class="sxs-lookup"><span data-stu-id="cc107-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="cc107-124">用於檢視 （格式） 的控制項的控制項的 name 元素</span><span class="sxs-lookup"><span data-stu-id="cc107-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="cc107-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc107-125">See Also</span></span>

[<span data-ttu-id="cc107-126">組態 （格式） 的控制項的控制項的 name 元素</span><span class="sxs-lookup"><span data-stu-id="cc107-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="cc107-127">用於檢視 （格式） 的控制項的控制項的 name 元素</span><span class="sxs-lookup"><span data-stu-id="cc107-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="cc107-128">ExpressionBinding CustomItem （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="cc107-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="cc107-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="cc107-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
