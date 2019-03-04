---
title: PropertyName ItemSelectionCondition 的 GroupBy （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858264"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="88a30-102">GroupBy 之 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="88a30-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="88a30-103">指定觸發條件的.NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="88a30-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="88a30-104">當這個屬性是存在，或當其評估結果為`true`、 符合條件，和使用控制項。</span><span class="sxs-lookup"><span data-stu-id="88a30-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="88a30-105">定義新的群組物件的顯示方式時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="88a30-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="88a30-106">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素CustomControl CustomEntry CustomItem 用於 GroupBy （格式） PropertyName 元素 ExpressionBinding 的 GroupBy （格式） ItemSelectionCondition 元素的 GroupBy （格式） ExpressionBinding 元素的 GroupBy （格式） CustomItem 元素GroupBy （格式） 的 ItemSelectionCondition</span><span class="sxs-lookup"><span data-stu-id="88a30-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="88a30-107">語法</span><span class="sxs-lookup"><span data-stu-id="88a30-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="88a30-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="88a30-108">Attributes and Elements</span></span>

<span data-ttu-id="88a30-109">下列各節說明屬性、 子項目和父項目`PropertyName`項目。</span><span class="sxs-lookup"><span data-stu-id="88a30-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="88a30-110">屬性</span><span class="sxs-lookup"><span data-stu-id="88a30-110">Attributes</span></span>

<span data-ttu-id="88a30-111">無。</span><span class="sxs-lookup"><span data-stu-id="88a30-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="88a30-112">子元素</span><span class="sxs-lookup"><span data-stu-id="88a30-112">Child Elements</span></span>

<span data-ttu-id="88a30-113">無。</span><span class="sxs-lookup"><span data-stu-id="88a30-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="88a30-114">父元素</span><span class="sxs-lookup"><span data-stu-id="88a30-114">Parent Elements</span></span>

|<span data-ttu-id="88a30-115">元素</span><span class="sxs-lookup"><span data-stu-id="88a30-115">Element</span></span>|<span data-ttu-id="88a30-116">描述</span><span class="sxs-lookup"><span data-stu-id="88a30-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="88a30-117">ItemSelectionCondition ExpressionBinding 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="88a30-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="88a30-118">定義要使用這個控制項必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="88a30-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="88a30-119">文字值</span><span class="sxs-lookup"><span data-stu-id="88a30-119">Text Value</span></span>

<span data-ttu-id="88a30-120">指定.NET 屬性觸發條件的名稱。</span><span class="sxs-lookup"><span data-stu-id="88a30-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="88a30-121">備註</span><span class="sxs-lookup"><span data-stu-id="88a30-121">Remarks</span></span>

<span data-ttu-id="88a30-122">如果會使用這個項目，您無法指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)時定義的選取項目條件的項目。</span><span class="sxs-lookup"><span data-stu-id="88a30-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="88a30-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88a30-123">See Also</span></span>

[<span data-ttu-id="88a30-124">GroupBy （格式） 的 ItemSelectionCondition 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="88a30-124">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="88a30-125">ItemSelectionCondition ExpressionBinding 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="88a30-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="88a30-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="88a30-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
