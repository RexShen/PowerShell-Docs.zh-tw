---
title: PropertyName ItemSelectionCondition 如 CustomControl 檢視 （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854784"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="41f93-102">檢視之 CustomControl 的 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="41f93-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="41f93-103">指定觸發條件的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="41f93-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="41f93-104">當這個屬性是存在，或當其評估結果為`true`、 符合條件，和使用控制項。</span><span class="sxs-lookup"><span data-stu-id="41f93-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="41f93-105">定義自訂控制項的檢視時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="41f93-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="41f93-106">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目 （格式） CustomEntries 項目 CustomControl CustomEntries 用於檢視 （格式） CustomItem 元素的檢視 （格式） CustomEntry 元素CustomEntry 檢視 （格式） 的檢視 （格式） ItemSelectionCondition 的項目運算式繫結的 ItemSelectionCondition 的檢視 （格式） PropertyName 元素 CustomControl CustomControl CustomItem ExpressionBinding 元素檢視 （格式 CustomControl</span><span class="sxs-lookup"><span data-stu-id="41f93-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="41f93-107">語法</span><span class="sxs-lookup"><span data-stu-id="41f93-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="41f93-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="41f93-108">Attributes and Elements</span></span>

<span data-ttu-id="41f93-109">下列各節說明屬性、 子項目和父項目`PropertyName`項目。</span><span class="sxs-lookup"><span data-stu-id="41f93-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="41f93-110">屬性</span><span class="sxs-lookup"><span data-stu-id="41f93-110">Attributes</span></span>

<span data-ttu-id="41f93-111">無。</span><span class="sxs-lookup"><span data-stu-id="41f93-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="41f93-112">子元素</span><span class="sxs-lookup"><span data-stu-id="41f93-112">Child Elements</span></span>

<span data-ttu-id="41f93-113">無。</span><span class="sxs-lookup"><span data-stu-id="41f93-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="41f93-114">父元素</span><span class="sxs-lookup"><span data-stu-id="41f93-114">Parent Elements</span></span>

|<span data-ttu-id="41f93-115">元素</span><span class="sxs-lookup"><span data-stu-id="41f93-115">Element</span></span>|<span data-ttu-id="41f93-116">描述</span><span class="sxs-lookup"><span data-stu-id="41f93-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="41f93-117">運算式繫結檢視 （格式） CustomControl ItemSelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="41f93-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="41f93-118">定義要使用這個控制項必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="41f93-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="41f93-119">文字值</span><span class="sxs-lookup"><span data-stu-id="41f93-119">Text Value</span></span>

<span data-ttu-id="41f93-120">指定.NET 屬性觸發條件的名稱。</span><span class="sxs-lookup"><span data-stu-id="41f93-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="41f93-121">備註</span><span class="sxs-lookup"><span data-stu-id="41f93-121">Remarks</span></span>

<span data-ttu-id="41f93-122">如果會使用這個項目，您無法指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)時定義的選取項目條件的項目。</span><span class="sxs-lookup"><span data-stu-id="41f93-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="41f93-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41f93-123">See Also</span></span>

[<span data-ttu-id="41f93-124">ItemSelectionCondition CustomControl 檢視 （格式） 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="41f93-124">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="41f93-125">運算式繫結檢視 （格式） CustomControl ItemSelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="41f93-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="41f93-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="41f93-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
