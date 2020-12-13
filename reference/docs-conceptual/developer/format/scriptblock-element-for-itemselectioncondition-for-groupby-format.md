---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)
description: GroupBy 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)
ms.openlocfilehash: fe366fa31b93e8d69409cc49c3fe2c350d4d06d9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665079"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="b70bf-103">GroupBy 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b70bf-103">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="b70bf-104">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="b70bf-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="b70bf-105">當此腳本評估為時 `true` ，就會符合條件，並且會使用控制項。</span><span class="sxs-lookup"><span data-stu-id="b70bf-105">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="b70bf-106">定義如何顯示新的物件群組時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="b70bf-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="b70bf-107">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy (格式) CustomEntries 元素適用于 CustomEntry 的 CustomControl 專案 (格式) CustomControl 元素針對 groupby (格式) CustomItem 元素，用於 CustomEntry 的 GroupBy (格式) ExpressionBinding 元素（CustomItem 的 groupby (格式）) ItemSelectionCondition 專案（ExpressionBinding 的 groupby (格式）)  (格式的 ItemSelectionCondition 專案) </span><span class="sxs-lookup"><span data-stu-id="b70bf-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b70bf-108">語法</span><span class="sxs-lookup"><span data-stu-id="b70bf-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b70bf-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b70bf-109">Attributes and Elements</span></span>

<span data-ttu-id="b70bf-110">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="b70bf-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b70bf-111">屬性</span><span class="sxs-lookup"><span data-stu-id="b70bf-111">Attributes</span></span>

<span data-ttu-id="b70bf-112">無。</span><span class="sxs-lookup"><span data-stu-id="b70bf-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b70bf-113">子元素</span><span class="sxs-lookup"><span data-stu-id="b70bf-113">Child Elements</span></span>

<span data-ttu-id="b70bf-114">無。</span><span class="sxs-lookup"><span data-stu-id="b70bf-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b70bf-115">父項目</span><span class="sxs-lookup"><span data-stu-id="b70bf-115">Parent Elements</span></span>

|<span data-ttu-id="b70bf-116">元素</span><span class="sxs-lookup"><span data-stu-id="b70bf-116">Element</span></span>|<span data-ttu-id="b70bf-117">描述</span><span class="sxs-lookup"><span data-stu-id="b70bf-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b70bf-118">GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b70bf-118">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="b70bf-119">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="b70bf-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b70bf-120">文字值</span><span class="sxs-lookup"><span data-stu-id="b70bf-120">Text Value</span></span>

<span data-ttu-id="b70bf-121">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="b70bf-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="b70bf-122">備註</span><span class="sxs-lookup"><span data-stu-id="b70bf-122">Remarks</span></span>

<span data-ttu-id="b70bf-123">如果使用此元素，則在定義選取條件時，不能指定 [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="b70bf-123">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="b70bf-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b70bf-124">See Also</span></span>

[<span data-ttu-id="b70bf-125">GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b70bf-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b70bf-126">GroupBy 之 ItemSelectionCondition 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b70bf-126">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="b70bf-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="b70bf-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
