---
title: 用於檢視 （格式） 的控制項 ItemSelectionCondition 的指令碼區塊項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064708"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="04b51-102">檢視之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="04b51-102">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="04b51-103">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="04b51-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="04b51-104">此指令碼會評估為`true`、 符合條件，和使用控制項。</span><span class="sxs-lookup"><span data-stu-id="04b51-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="04b51-105">定義可供檢視的控制項時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="04b51-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="04b51-106">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目CustomControl CustomEntries CustomEntry CustomItem 用於檢視 （格式） 的控制項的檢視 （格式） ExpressionBinding 元素的控制項的檢視 （格式） CustomItem 元素的控制項的檢視 （格式） CustomEntry 元素ItemSelectionCondition ExpressionBinding ItemSelectionCondition 用於檢視 （格式） 的控制項的檢視 （格式） ScriptBlock 元素的控制項項目</span><span class="sxs-lookup"><span data-stu-id="04b51-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="04b51-107">語法</span><span class="sxs-lookup"><span data-stu-id="04b51-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="04b51-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="04b51-108">Attributes and Elements</span></span>

<span data-ttu-id="04b51-109">下列各節說明屬性、 子項目和父項目`ScriptBlock`項目。</span><span class="sxs-lookup"><span data-stu-id="04b51-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="04b51-110">屬性</span><span class="sxs-lookup"><span data-stu-id="04b51-110">Attributes</span></span>

<span data-ttu-id="04b51-111">無。</span><span class="sxs-lookup"><span data-stu-id="04b51-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="04b51-112">子元素</span><span class="sxs-lookup"><span data-stu-id="04b51-112">Child Elements</span></span>

<span data-ttu-id="04b51-113">無。</span><span class="sxs-lookup"><span data-stu-id="04b51-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="04b51-114">父項目</span><span class="sxs-lookup"><span data-stu-id="04b51-114">Parent Elements</span></span>

|<span data-ttu-id="04b51-115">項目</span><span class="sxs-lookup"><span data-stu-id="04b51-115">Element</span></span>|<span data-ttu-id="04b51-116">描述</span><span class="sxs-lookup"><span data-stu-id="04b51-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="04b51-117">用於檢視 （格式） 的控制項 ExpressionBinding ItemSelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="04b51-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="04b51-118">定義要使用這個控制項必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="04b51-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="04b51-119">文字值</span><span class="sxs-lookup"><span data-stu-id="04b51-119">Text Value</span></span>

<span data-ttu-id="04b51-120">指定評估指令碼。</span><span class="sxs-lookup"><span data-stu-id="04b51-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="04b51-121">備註</span><span class="sxs-lookup"><span data-stu-id="04b51-121">Remarks</span></span>

<span data-ttu-id="04b51-122">如果會使用這個項目，您無法指定[PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)時定義的選取項目條件的項目。</span><span class="sxs-lookup"><span data-stu-id="04b51-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="04b51-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04b51-123">See Also</span></span>

[<span data-ttu-id="04b51-124">PropertyName ItemSelectionCondition 用於檢視 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="04b51-124">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="04b51-125">用於檢視 （格式） 的控制項 ExpressionBinding ItemSelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="04b51-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="04b51-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="04b51-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
