---
title: ItemSelectionCondition for CustomControl for View 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362437"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="97cf7-102">檢視之 CustomControl 的 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="97cf7-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="97cf7-103">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="97cf7-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="97cf7-104">當這個屬性存在或評估為 `true` 時，就會符合條件，並使用控制項。</span><span class="sxs-lookup"><span data-stu-id="97cf7-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="97cf7-105">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="97cf7-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="97cf7-106">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素（format） CustomEntries 元素，用於 CustomEntry for View （Format） CustomEntries 元素的 CustomControl for view （format） CustomItem 元素CustomEntry for view （Format） ExpressionBinding 元素 for CustomControl for view （format） ItemSelectionCondition 元素 for CustomControl for View （Format） PropertyName 元素CustomControl for View （格式</span><span class="sxs-lookup"><span data-stu-id="97cf7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="97cf7-107">語法</span><span class="sxs-lookup"><span data-stu-id="97cf7-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="97cf7-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="97cf7-108">Attributes and Elements</span></span>

<span data-ttu-id="97cf7-109">下列各節說明屬性、子專案，以及 `PropertyName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="97cf7-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="97cf7-110">屬性</span><span class="sxs-lookup"><span data-stu-id="97cf7-110">Attributes</span></span>

<span data-ttu-id="97cf7-111">無。</span><span class="sxs-lookup"><span data-stu-id="97cf7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="97cf7-112">子元素</span><span class="sxs-lookup"><span data-stu-id="97cf7-112">Child Elements</span></span>

<span data-ttu-id="97cf7-113">無。</span><span class="sxs-lookup"><span data-stu-id="97cf7-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="97cf7-114">父元素</span><span class="sxs-lookup"><span data-stu-id="97cf7-114">Parent Elements</span></span>

|<span data-ttu-id="97cf7-115">元素</span><span class="sxs-lookup"><span data-stu-id="97cf7-115">Element</span></span>|<span data-ttu-id="97cf7-116">描述</span><span class="sxs-lookup"><span data-stu-id="97cf7-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="97cf7-117">CustomControl for View 的運算式系結的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="97cf7-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="97cf7-118">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="97cf7-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="97cf7-119">文字值</span><span class="sxs-lookup"><span data-stu-id="97cf7-119">Text Value</span></span>

<span data-ttu-id="97cf7-120">指定觸發條件之 .NET 屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="97cf7-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="97cf7-121">備註</span><span class="sxs-lookup"><span data-stu-id="97cf7-121">Remarks</span></span>

<span data-ttu-id="97cf7-122">如果使用這個元素，則在定義選取條件時，不能指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="97cf7-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="97cf7-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97cf7-123">See Also</span></span>

[<span data-ttu-id="97cf7-124">ItemSelectionCondition for CustomControl for View 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="97cf7-124">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="97cf7-125">CustomControl for View 的運算式系結的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="97cf7-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="97cf7-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="97cf7-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
