---
title: View 之控制項的 ExpressionBinding 的 CustomControlName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369147"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="be2bc-102">檢視之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="be2bc-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="be2bc-103">指定通用控制項或 view 控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="be2bc-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="be2bc-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="be2bc-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="be2bc-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素CustomControl for View （format） CustomEntry 元素 for CustomEntries for view （format） CustomItem 元素 for view （format） CustomEntry 元素 for view （格式） ExpressionBinding 的控制項View 之控制項的 ExpressionBindine 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="be2bc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="be2bc-106">語法</span><span class="sxs-lookup"><span data-stu-id="be2bc-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="be2bc-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="be2bc-107">Attributes and Elements</span></span>

<span data-ttu-id="be2bc-108">下列各節說明屬性、子專案，以及 `CustomControlName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="be2bc-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="be2bc-109">屬性</span><span class="sxs-lookup"><span data-stu-id="be2bc-109">Attributes</span></span>

<span data-ttu-id="be2bc-110">無。</span><span class="sxs-lookup"><span data-stu-id="be2bc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="be2bc-111">子元素</span><span class="sxs-lookup"><span data-stu-id="be2bc-111">Child Elements</span></span>

<span data-ttu-id="be2bc-112">無。</span><span class="sxs-lookup"><span data-stu-id="be2bc-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="be2bc-113">父元素</span><span class="sxs-lookup"><span data-stu-id="be2bc-113">Parent Elements</span></span>

|<span data-ttu-id="be2bc-114">元素</span><span class="sxs-lookup"><span data-stu-id="be2bc-114">Element</span></span>|<span data-ttu-id="be2bc-115">描述</span><span class="sxs-lookup"><span data-stu-id="be2bc-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="be2bc-116">View 之控制項的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="be2bc-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="be2bc-117">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="be2bc-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="be2bc-118">文字值</span><span class="sxs-lookup"><span data-stu-id="be2bc-118">Text Value</span></span>

<span data-ttu-id="be2bc-119">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="be2bc-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="be2bc-120">備註</span><span class="sxs-lookup"><span data-stu-id="be2bc-120">Remarks</span></span>

<span data-ttu-id="be2bc-121">您可以建立可供格式化檔案的所有視圖使用的通用控制項，而且可以建立可供特定視圖使用的 view 控制項。</span><span class="sxs-lookup"><span data-stu-id="be2bc-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="be2bc-122">下列元素會指定這些控制項的名稱：</span><span class="sxs-lookup"><span data-stu-id="be2bc-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="be2bc-123">設定之控制項的控制項的名稱元素（格式）</span><span class="sxs-lookup"><span data-stu-id="be2bc-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="be2bc-124">View 控制項控制項的 Name 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="be2bc-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="be2bc-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be2bc-125">See Also</span></span>

[<span data-ttu-id="be2bc-126">設定之控制項的控制項的名稱元素（格式）</span><span class="sxs-lookup"><span data-stu-id="be2bc-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="be2bc-127">View 控制項控制項的 Name 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="be2bc-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="be2bc-128">View 之控制項的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="be2bc-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="be2bc-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="be2bc-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
