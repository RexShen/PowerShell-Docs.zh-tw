---
title: ScriptBlock ItemSeclectionCondition 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51f7aec9-7b01-4370-84f4-1e58508a851f
caps.latest.revision: 6
ms.openlocfilehash: e92b2dfff07358132c480c47c34279e5365fe400
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064436"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="3bc8f-102">設定之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3bc8f-102">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="3bc8f-103">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="3bc8f-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="3bc8f-104">此指令碼會評估為`true`、 符合條件，和使用控制項。</span><span class="sxs-lookup"><span data-stu-id="3bc8f-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="3bc8f-105">定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="3bc8f-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="3bc8f-106">組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目CustomControl CustomEntry CustomItem 組態 （格式） 的控制項設定 ExpressionBinding 元素的控制項的組態 （格式） CustomItem 元素的控制項的格式） CustomEntry 項目ItemSelectionCondition ExpressionBinding 的 ItemSelectionCondition 控制項組態 （格式） 的組態 （格式） 指令碼區塊項目控制項的項目</span><span class="sxs-lookup"><span data-stu-id="3bc8f-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3bc8f-107">語法</span><span class="sxs-lookup"><span data-stu-id="3bc8f-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3bc8f-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3bc8f-108">Attributes and Elements</span></span>

<span data-ttu-id="3bc8f-109">下列各節說明屬性、 子項目和父項目`ScriptBlock`項目。</span><span class="sxs-lookup"><span data-stu-id="3bc8f-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3bc8f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="3bc8f-110">Attributes</span></span>

<span data-ttu-id="3bc8f-111">無。</span><span class="sxs-lookup"><span data-stu-id="3bc8f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3bc8f-112">子元素</span><span class="sxs-lookup"><span data-stu-id="3bc8f-112">Child Elements</span></span>

<span data-ttu-id="3bc8f-113">無。</span><span class="sxs-lookup"><span data-stu-id="3bc8f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3bc8f-114">父項目</span><span class="sxs-lookup"><span data-stu-id="3bc8f-114">Parent Elements</span></span>

|<span data-ttu-id="3bc8f-115">項目</span><span class="sxs-lookup"><span data-stu-id="3bc8f-115">Element</span></span>|<span data-ttu-id="3bc8f-116">描述</span><span class="sxs-lookup"><span data-stu-id="3bc8f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3bc8f-117">ItemSelectionCondition ExpressionBinding 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="3bc8f-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="3bc8f-118">定義要使用這個控制項必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="3bc8f-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3bc8f-119">文字值</span><span class="sxs-lookup"><span data-stu-id="3bc8f-119">Text Value</span></span>

<span data-ttu-id="3bc8f-120">指定評估指令碼。</span><span class="sxs-lookup"><span data-stu-id="3bc8f-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="3bc8f-121">備註</span><span class="sxs-lookup"><span data-stu-id="3bc8f-121">Remarks</span></span>

<span data-ttu-id="3bc8f-122">如果會使用這個項目，您無法指定[PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)時定義的選取項目條件的項目。</span><span class="sxs-lookup"><span data-stu-id="3bc8f-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="3bc8f-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bc8f-123">See Also</span></span>

[<span data-ttu-id="3bc8f-124">PropertyName ItemSeclectionCondition 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="3bc8f-124">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="3bc8f-125">ItemSelectionCondition ExpressionBinding 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="3bc8f-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="3bc8f-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="3bc8f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
