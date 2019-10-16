---
title: 設定之控制項的 Itemselectioncondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51f7aec9-7b01-4370-84f4-1e58508a851f
caps.latest.revision: 6
ms.openlocfilehash: e92b2dfff07358132c480c47c34279e5365fe400
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362117"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="940f9-102">設定之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="940f9-102">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="940f9-103">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="940f9-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="940f9-104">當此腳本評估為 `true` 時，就會符合條件，並使用控制項。</span><span class="sxs-lookup"><span data-stu-id="940f9-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="940f9-105">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="940f9-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="940f9-106">Configuration 元素（格式）控制設定（format） CustomControl 元素的設定（格式）控制項專案的設定專案（格式） CustomControl 設定的 CustomEntries 元素（格式）Format） CustomEntry 元素，用於 CustomControl 控制項的 CustomItem 元素，用於 CustomEntry 的 configuration ExpressionBinding 元素設定的 CustomItem 專案的控制項（格式）ExpressionBinding 的 ItemSelectionCondition 元素，用於 ItemSelectionCondition 用於設定之控制項的設定（格式） ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="940f9-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="940f9-107">語法</span><span class="sxs-lookup"><span data-stu-id="940f9-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="940f9-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="940f9-108">Attributes and Elements</span></span>

<span data-ttu-id="940f9-109">下列各節說明屬性、子專案，以及 `ScriptBlock` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="940f9-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="940f9-110">屬性</span><span class="sxs-lookup"><span data-stu-id="940f9-110">Attributes</span></span>

<span data-ttu-id="940f9-111">無。</span><span class="sxs-lookup"><span data-stu-id="940f9-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="940f9-112">子元素</span><span class="sxs-lookup"><span data-stu-id="940f9-112">Child Elements</span></span>

<span data-ttu-id="940f9-113">無。</span><span class="sxs-lookup"><span data-stu-id="940f9-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="940f9-114">父元素</span><span class="sxs-lookup"><span data-stu-id="940f9-114">Parent Elements</span></span>

|<span data-ttu-id="940f9-115">元素</span><span class="sxs-lookup"><span data-stu-id="940f9-115">Element</span></span>|<span data-ttu-id="940f9-116">描述</span><span class="sxs-lookup"><span data-stu-id="940f9-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="940f9-117">設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="940f9-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="940f9-118">定義必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="940f9-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="940f9-119">文字值</span><span class="sxs-lookup"><span data-stu-id="940f9-119">Text Value</span></span>

<span data-ttu-id="940f9-120">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="940f9-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="940f9-121">備註</span><span class="sxs-lookup"><span data-stu-id="940f9-121">Remarks</span></span>

<span data-ttu-id="940f9-122">如果使用這個元素，則在定義選取條件時，不能指定[PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="940f9-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="940f9-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="940f9-123">See Also</span></span>

[<span data-ttu-id="940f9-124">設定之控制項的 Itemselectioncondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="940f9-124">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="940f9-125">設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="940f9-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="940f9-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="940f9-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
