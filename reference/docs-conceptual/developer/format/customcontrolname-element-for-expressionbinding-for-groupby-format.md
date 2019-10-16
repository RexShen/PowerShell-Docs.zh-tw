---
title: GroupBy 之 ExpressionBinding 的 CustomControlName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368907"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="0056a-102">GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0056a-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="0056a-103">指定通用控制項或 view 控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="0056a-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="0056a-104">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="0056a-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="0056a-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（format） CustomEntries 專案的 groupby （format） CustomControl 元素，適用于的 CustomControl for GroupBy （format） CustomEntry 元素適用于 CustomItem for groupby （format） CustomControlName 元素的 groupby （format） ExpressionBinding 元素的 GroupBy （格式） CustomItem 元素的 CustomControl</span><span class="sxs-lookup"><span data-stu-id="0056a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0056a-106">語法</span><span class="sxs-lookup"><span data-stu-id="0056a-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0056a-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="0056a-107">Attributes and Elements</span></span>

<span data-ttu-id="0056a-108">下列各節說明屬性、子專案，以及 `CustomControlName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="0056a-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0056a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="0056a-109">Attributes</span></span>

<span data-ttu-id="0056a-110">無。</span><span class="sxs-lookup"><span data-stu-id="0056a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0056a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="0056a-111">Child Elements</span></span>

<span data-ttu-id="0056a-112">無。</span><span class="sxs-lookup"><span data-stu-id="0056a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0056a-113">父元素</span><span class="sxs-lookup"><span data-stu-id="0056a-113">Parent Elements</span></span>

|<span data-ttu-id="0056a-114">元素</span><span class="sxs-lookup"><span data-stu-id="0056a-114">Element</span></span>|<span data-ttu-id="0056a-115">描述</span><span class="sxs-lookup"><span data-stu-id="0056a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0056a-116">GroupBy 之 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0056a-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="0056a-117">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="0056a-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0056a-118">文字值</span><span class="sxs-lookup"><span data-stu-id="0056a-118">Text Value</span></span>

<span data-ttu-id="0056a-119">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="0056a-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="0056a-120">備註</span><span class="sxs-lookup"><span data-stu-id="0056a-120">Remarks</span></span>

<span data-ttu-id="0056a-121">您可以建立可供格式化檔案的所有視圖使用的通用控制項，而且可以建立可供特定視圖使用的 view 控制項。</span><span class="sxs-lookup"><span data-stu-id="0056a-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="0056a-122">下列元素會指定這些控制項的名稱：</span><span class="sxs-lookup"><span data-stu-id="0056a-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="0056a-123">設定之控制項的控制項的名稱元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0056a-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="0056a-124">View 控制項控制項的 Name 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0056a-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="0056a-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0056a-125">See Also</span></span>

[<span data-ttu-id="0056a-126">設定之控制項的控制項的名稱元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0056a-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="0056a-127">View 控制項控制項的 Name 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0056a-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="0056a-128">GroupBy 之 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0056a-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="0056a-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="0056a-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
