---
title: ItemSelectionCondition CustomControl 檢視 （格式） 的指令碼區塊項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064470"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="86079-102">檢視之 CustomControl 的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="86079-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="86079-103">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="86079-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="86079-104">此指令碼會評估為`true`、 符合條件，和使用控制項。</span><span class="sxs-lookup"><span data-stu-id="86079-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="86079-105">定義自訂控制項的檢視時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="86079-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="86079-106">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目 （格式） CustomEntries 項目 CustomControl CustomEntries 用於檢視 （格式） CustomItem 元素的檢視 （格式） CustomEntry 元素CustomEntry 檢視 （格式） 的檢視 （格式） ItemSelectionCondition 的項目運算式繫結的 ItemSelectionCondition 的檢視 （格式） ScriptBlock 元素 CustomControl CustomControl CustomItem ExpressionBinding 元素CustomControl 檢視 （格式）</span><span class="sxs-lookup"><span data-stu-id="86079-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="86079-107">語法</span><span class="sxs-lookup"><span data-stu-id="86079-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="86079-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="86079-108">Attributes and Elements</span></span>

<span data-ttu-id="86079-109">下列各節說明屬性、 子項目和父項目`ScriptBlock`項目。</span><span class="sxs-lookup"><span data-stu-id="86079-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="86079-110">屬性</span><span class="sxs-lookup"><span data-stu-id="86079-110">Attributes</span></span>

<span data-ttu-id="86079-111">無。</span><span class="sxs-lookup"><span data-stu-id="86079-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="86079-112">子元素</span><span class="sxs-lookup"><span data-stu-id="86079-112">Child Elements</span></span>

<span data-ttu-id="86079-113">無。</span><span class="sxs-lookup"><span data-stu-id="86079-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="86079-114">父項目</span><span class="sxs-lookup"><span data-stu-id="86079-114">Parent Elements</span></span>

|<span data-ttu-id="86079-115">項目</span><span class="sxs-lookup"><span data-stu-id="86079-115">Element</span></span>|<span data-ttu-id="86079-116">描述</span><span class="sxs-lookup"><span data-stu-id="86079-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86079-117">運算式繫結檢視 （格式） CustomControl ItemSelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="86079-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="86079-118">定義要使用這個控制項必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="86079-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="86079-119">文字值</span><span class="sxs-lookup"><span data-stu-id="86079-119">Text Value</span></span>

<span data-ttu-id="86079-120">指定評估指令碼。</span><span class="sxs-lookup"><span data-stu-id="86079-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="86079-121">備註</span><span class="sxs-lookup"><span data-stu-id="86079-121">Remarks</span></span>

<span data-ttu-id="86079-122">如果會使用這個項目，您無法指定[PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)時定義的選取項目條件的項目。</span><span class="sxs-lookup"><span data-stu-id="86079-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="86079-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86079-123">See Also</span></span>

[<span data-ttu-id="86079-124">PropertyName ItemSelectionCondition 如 CustomControl 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="86079-124">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="86079-125">運算式繫結檢視 （格式） CustomControl ItemSelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="86079-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="86079-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="86079-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
