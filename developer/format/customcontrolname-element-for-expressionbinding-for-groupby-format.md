---
title: CustomControlName ExpressionBinding 的 GroupBy （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066561"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="1452d-102">GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1452d-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="1452d-103">指定通用控制項的檢視控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="1452d-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="1452d-104">定義新的群組物件的顯示方式時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="1452d-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="1452d-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素CustomControl CustomEntry CustomItem ExpressionBinding 的 GroupBy （格式） 的 GroupBy （格式） CustomControlName 元素的 GroupBy （格式） ExpressionBinding 元素的 GroupBy （格式） CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="1452d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1452d-106">語法</span><span class="sxs-lookup"><span data-stu-id="1452d-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1452d-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1452d-107">Attributes and Elements</span></span>

<span data-ttu-id="1452d-108">下列各節說明屬性、 子項目和父項目`CustomControlName`項目。</span><span class="sxs-lookup"><span data-stu-id="1452d-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1452d-109">屬性</span><span class="sxs-lookup"><span data-stu-id="1452d-109">Attributes</span></span>

<span data-ttu-id="1452d-110">無。</span><span class="sxs-lookup"><span data-stu-id="1452d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1452d-111">子元素</span><span class="sxs-lookup"><span data-stu-id="1452d-111">Child Elements</span></span>

<span data-ttu-id="1452d-112">無。</span><span class="sxs-lookup"><span data-stu-id="1452d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1452d-113">父項目</span><span class="sxs-lookup"><span data-stu-id="1452d-113">Parent Elements</span></span>

|<span data-ttu-id="1452d-114">項目</span><span class="sxs-lookup"><span data-stu-id="1452d-114">Element</span></span>|<span data-ttu-id="1452d-115">描述</span><span class="sxs-lookup"><span data-stu-id="1452d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1452d-116">ExpressionBinding CustomItem 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="1452d-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="1452d-117">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="1452d-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1452d-118">文字值</span><span class="sxs-lookup"><span data-stu-id="1452d-118">Text Value</span></span>

<span data-ttu-id="1452d-119">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="1452d-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="1452d-120">備註</span><span class="sxs-lookup"><span data-stu-id="1452d-120">Remarks</span></span>

<span data-ttu-id="1452d-121">您可以建立可供所有的格式化檔案，檢視的通用控制項，而且您可以建立可供特定檢視的檢視控制項。</span><span class="sxs-lookup"><span data-stu-id="1452d-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="1452d-122">下列項目會指定這些控制項的名稱：</span><span class="sxs-lookup"><span data-stu-id="1452d-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="1452d-123">組態 （格式） 的控制項的控制項的 name 元素</span><span class="sxs-lookup"><span data-stu-id="1452d-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="1452d-124">用於檢視 （格式） 的控制項的控制項的 name 元素</span><span class="sxs-lookup"><span data-stu-id="1452d-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="1452d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1452d-125">See Also</span></span>

[<span data-ttu-id="1452d-126">組態 （格式） 的控制項的控制項的 name 元素</span><span class="sxs-lookup"><span data-stu-id="1452d-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="1452d-127">用於檢視 （格式） 的控制項的控制項的 name 元素</span><span class="sxs-lookup"><span data-stu-id="1452d-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="1452d-128">ExpressionBinding CustomItem 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="1452d-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="1452d-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="1452d-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
