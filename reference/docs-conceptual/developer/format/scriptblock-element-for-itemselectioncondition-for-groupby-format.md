---
title: GroupBy 的 ItemSelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364827"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="b9e91-102">GroupBy 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b9e91-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="b9e91-103">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="b9e91-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="b9e91-104">當此腳本評估為 `true` 時，就會符合條件，並使用控制項。</span><span class="sxs-lookup"><span data-stu-id="b9e91-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="b9e91-105">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="b9e91-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="b9e91-106">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（format） CustomEntries 專案的 groupby （format） CustomControl 元素，適用于的 CustomControl for GroupBy （format） CustomEntry 元素CustomControl 適用于 CustomEntry for groupby （format） CustomItem 元素的 groupby （format） CustomItem 元素，適用于 ItemSelectionCondition 的 groupby （格式） ScriptBlock 元素GroupBy 的 ItemSelectionCondition （格式）</span><span class="sxs-lookup"><span data-stu-id="b9e91-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b9e91-107">語法</span><span class="sxs-lookup"><span data-stu-id="b9e91-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b9e91-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="b9e91-108">Attributes and Elements</span></span>

<span data-ttu-id="b9e91-109">下列各節說明屬性、子專案，以及 `ScriptBlock` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="b9e91-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b9e91-110">屬性</span><span class="sxs-lookup"><span data-stu-id="b9e91-110">Attributes</span></span>

<span data-ttu-id="b9e91-111">無。</span><span class="sxs-lookup"><span data-stu-id="b9e91-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b9e91-112">子元素</span><span class="sxs-lookup"><span data-stu-id="b9e91-112">Child Elements</span></span>

<span data-ttu-id="b9e91-113">無。</span><span class="sxs-lookup"><span data-stu-id="b9e91-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b9e91-114">父元素</span><span class="sxs-lookup"><span data-stu-id="b9e91-114">Parent Elements</span></span>

|<span data-ttu-id="b9e91-115">元素</span><span class="sxs-lookup"><span data-stu-id="b9e91-115">Element</span></span>|<span data-ttu-id="b9e91-116">描述</span><span class="sxs-lookup"><span data-stu-id="b9e91-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b9e91-117">GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b9e91-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="b9e91-118">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="b9e91-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b9e91-119">文字值</span><span class="sxs-lookup"><span data-stu-id="b9e91-119">Text Value</span></span>

<span data-ttu-id="b9e91-120">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="b9e91-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9e91-121">備註</span><span class="sxs-lookup"><span data-stu-id="b9e91-121">Remarks</span></span>

<span data-ttu-id="b9e91-122">如果使用這個元素，則在定義選取條件時，不能指定[PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="b9e91-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9e91-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9e91-123">See Also</span></span>

[<span data-ttu-id="b9e91-124">GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b9e91-124">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b9e91-125">GroupBy 之 ItemSelectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="b9e91-125">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="b9e91-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="b9e91-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
