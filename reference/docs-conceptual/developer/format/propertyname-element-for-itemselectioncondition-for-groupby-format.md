---
title: GroupBy 之 ItemSelectionCondition 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362407"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="03e6b-102">GroupBy 之 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="03e6b-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="03e6b-103">指定觸發條件的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="03e6b-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="03e6b-104">當這個屬性存在或評估為 `true`時，就會符合條件，並使用控制項。</span><span class="sxs-lookup"><span data-stu-id="03e6b-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="03e6b-105">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="03e6b-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="03e6b-106">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（format） CustomEntries 專案的 groupby （format） CustomControl 元素，適用于的 CustomControl for GroupBy （format） CustomEntry 元素適用于 CustomEntry 之 groupby （format） ExpressionBinding 元素的 GroupBy （format） CustomItem 元素的 CustomControl，適用于 CustomItem 的 groupby （格式） ItemSelectionCondition 元素。GroupBy 的 ItemSelectionCondition （格式）</span><span class="sxs-lookup"><span data-stu-id="03e6b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="03e6b-107">語法</span><span class="sxs-lookup"><span data-stu-id="03e6b-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="03e6b-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="03e6b-108">Attributes and Elements</span></span>

<span data-ttu-id="03e6b-109">下列各節說明屬性、子專案，以及 `PropertyName` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="03e6b-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="03e6b-110">屬性</span><span class="sxs-lookup"><span data-stu-id="03e6b-110">Attributes</span></span>

<span data-ttu-id="03e6b-111">無。</span><span class="sxs-lookup"><span data-stu-id="03e6b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="03e6b-112">子元素</span><span class="sxs-lookup"><span data-stu-id="03e6b-112">Child Elements</span></span>

<span data-ttu-id="03e6b-113">無。</span><span class="sxs-lookup"><span data-stu-id="03e6b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="03e6b-114">父元素</span><span class="sxs-lookup"><span data-stu-id="03e6b-114">Parent Elements</span></span>

|<span data-ttu-id="03e6b-115">元素</span><span class="sxs-lookup"><span data-stu-id="03e6b-115">Element</span></span>|<span data-ttu-id="03e6b-116">描述</span><span class="sxs-lookup"><span data-stu-id="03e6b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="03e6b-117">GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="03e6b-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="03e6b-118">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="03e6b-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="03e6b-119">文字值</span><span class="sxs-lookup"><span data-stu-id="03e6b-119">Text Value</span></span>

<span data-ttu-id="03e6b-120">指定觸發條件之 .NET 屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="03e6b-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="03e6b-121">備註</span><span class="sxs-lookup"><span data-stu-id="03e6b-121">Remarks</span></span>

<span data-ttu-id="03e6b-122">如果使用這個元素，則在定義選取條件時，不能指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="03e6b-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="03e6b-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03e6b-123">See Also</span></span>

[<span data-ttu-id="03e6b-124">GroupBy 的 ItemSelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="03e6b-124">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="03e6b-125">GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="03e6b-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="03e6b-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="03e6b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
