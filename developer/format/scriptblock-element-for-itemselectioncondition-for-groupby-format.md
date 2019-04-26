---
title: GroupBy （格式） 的 ItemSelectionCondition 的指令碼區塊項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064538"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="6a9d4-102">GroupBy 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="6a9d4-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="6a9d4-103">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="6a9d4-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="6a9d4-104">此指令碼會評估為`true`、 符合條件，和使用控制項。</span><span class="sxs-lookup"><span data-stu-id="6a9d4-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="6a9d4-105">定義新的群組物件的顯示方式時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="6a9d4-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="6a9d4-106">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素CustomControl CustomEntry CustomItem 用於 GroupBy （格式） ScriptBlock 元素 ExpressionBinding 的 GroupBy （格式） ItemSelectionCondition 元素的 GroupBy （格式） ExpressionBinding 元素的 GroupBy （格式） CustomItem 元素GroupBy （格式） 的 ItemSelectionCondition</span><span class="sxs-lookup"><span data-stu-id="6a9d4-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6a9d4-107">語法</span><span class="sxs-lookup"><span data-stu-id="6a9d4-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6a9d4-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6a9d4-108">Attributes and Elements</span></span>

<span data-ttu-id="6a9d4-109">下列各節說明屬性、 子項目和父項目`ScriptBlock`項目。</span><span class="sxs-lookup"><span data-stu-id="6a9d4-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6a9d4-110">屬性</span><span class="sxs-lookup"><span data-stu-id="6a9d4-110">Attributes</span></span>

<span data-ttu-id="6a9d4-111">無。</span><span class="sxs-lookup"><span data-stu-id="6a9d4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6a9d4-112">子元素</span><span class="sxs-lookup"><span data-stu-id="6a9d4-112">Child Elements</span></span>

<span data-ttu-id="6a9d4-113">無。</span><span class="sxs-lookup"><span data-stu-id="6a9d4-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6a9d4-114">父項目</span><span class="sxs-lookup"><span data-stu-id="6a9d4-114">Parent Elements</span></span>

|<span data-ttu-id="6a9d4-115">項目</span><span class="sxs-lookup"><span data-stu-id="6a9d4-115">Element</span></span>|<span data-ttu-id="6a9d4-116">描述</span><span class="sxs-lookup"><span data-stu-id="6a9d4-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a9d4-117">ItemSelectionCondition ExpressionBinding 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="6a9d4-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="6a9d4-118">定義要使用這個控制項必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="6a9d4-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6a9d4-119">文字值</span><span class="sxs-lookup"><span data-stu-id="6a9d4-119">Text Value</span></span>

<span data-ttu-id="6a9d4-120">指定評估指令碼。</span><span class="sxs-lookup"><span data-stu-id="6a9d4-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="6a9d4-121">備註</span><span class="sxs-lookup"><span data-stu-id="6a9d4-121">Remarks</span></span>

<span data-ttu-id="6a9d4-122">如果會使用這個項目，您無法指定[PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)時定義的選取項目條件的項目。</span><span class="sxs-lookup"><span data-stu-id="6a9d4-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a9d4-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a9d4-123">See Also</span></span>

[<span data-ttu-id="6a9d4-124">ItemSelectionCondition ExpressionBinding 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="6a9d4-124">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="6a9d4-125">PropertyName ItemSelectionCondition 的 GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="6a9d4-125">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="6a9d4-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="6a9d4-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
