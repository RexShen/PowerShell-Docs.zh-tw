---
title: CustomControl for View 的 ExpressionBinding 的 CustomControlName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364107"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="48e3d-102">檢視之 CustomControl 的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="48e3d-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="48e3d-103">指定通用控制項或 view 控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="48e3d-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="48e3d-104">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="48e3d-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="48e3d-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl Element for view （format） CustomEntries Element for view （format） CustomEntry for View （format） CustomEntries 元素CustomEntry for View （Format） ExpressionBinding 元素的元素，適用于 CustomItem 的運算式系結的 CustomItem （Format） CustomControlName 元素</span><span class="sxs-lookup"><span data-stu-id="48e3d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="48e3d-106">語法</span><span class="sxs-lookup"><span data-stu-id="48e3d-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="48e3d-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="48e3d-107">Attributes and Elements</span></span>

<span data-ttu-id="48e3d-108">下列各節說明屬性、子專案，以及 `CustomControlName` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="48e3d-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="48e3d-109">屬性</span><span class="sxs-lookup"><span data-stu-id="48e3d-109">Attributes</span></span>

<span data-ttu-id="48e3d-110">無。</span><span class="sxs-lookup"><span data-stu-id="48e3d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="48e3d-111">子元素</span><span class="sxs-lookup"><span data-stu-id="48e3d-111">Child Elements</span></span>

<span data-ttu-id="48e3d-112">無。</span><span class="sxs-lookup"><span data-stu-id="48e3d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="48e3d-113">父元素</span><span class="sxs-lookup"><span data-stu-id="48e3d-113">Parent Elements</span></span>

|<span data-ttu-id="48e3d-114">元素</span><span class="sxs-lookup"><span data-stu-id="48e3d-114">Element</span></span>|<span data-ttu-id="48e3d-115">描述</span><span class="sxs-lookup"><span data-stu-id="48e3d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="48e3d-116">CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="48e3d-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="48e3d-117">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="48e3d-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="48e3d-118">文字值</span><span class="sxs-lookup"><span data-stu-id="48e3d-118">Text Value</span></span>

<span data-ttu-id="48e3d-119">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="48e3d-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="48e3d-120">備註</span><span class="sxs-lookup"><span data-stu-id="48e3d-120">Remarks</span></span>

<span data-ttu-id="48e3d-121">您可以建立可供格式化檔案的所有視圖使用的通用控制項，而且可以建立可供特定視圖使用的 view 控制項。</span><span class="sxs-lookup"><span data-stu-id="48e3d-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="48e3d-122">這些控制項的名稱是由下列元素所指定。</span><span class="sxs-lookup"><span data-stu-id="48e3d-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="48e3d-123">設定之控制項的控制項的名稱元素（格式）</span><span class="sxs-lookup"><span data-stu-id="48e3d-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="48e3d-124">View 控制項控制項的 Name 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="48e3d-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="48e3d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48e3d-125">See Also</span></span>

[<span data-ttu-id="48e3d-126">設定之控制項的控制項的名稱元素（格式）</span><span class="sxs-lookup"><span data-stu-id="48e3d-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="48e3d-127">View 控制項控制項的 Name 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="48e3d-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="48e3d-128">CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="48e3d-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="48e3d-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="48e3d-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
