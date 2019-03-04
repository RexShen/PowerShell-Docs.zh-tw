---
title: ItemSelectionCondition ListControl （格式） 的指令碼區塊項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855414"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="a7e78-102">ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a7e78-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="a7e78-103">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="a7e78-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="a7e78-104">此指令碼會評估為`true`、 符合條件，和使用的清單項目。</span><span class="sxs-lookup"><span data-stu-id="a7e78-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="a7e78-105">定義清單檢視時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="a7e78-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="a7e78-106">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 ListEntry ListControl （格式） ListItems 元素 ListEntries ListControl （格式） ListEntry 項目用於 ListItem ListControl （格式） 的 ItemSelectionCondition ListControl （格式） ScriptBlock 元素的清單控制項 （格式） ItemSelectionCondition 元素 ListItems ListControl （格式） ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="a7e78-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a7e78-107">語法</span><span class="sxs-lookup"><span data-stu-id="a7e78-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a7e78-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="a7e78-108">Attributes and Elements</span></span>

<span data-ttu-id="a7e78-109">下列各節說明屬性、 子項目，以及的父項目`ScriptBlock`項目。</span><span class="sxs-lookup"><span data-stu-id="a7e78-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a7e78-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a7e78-110">Attributes</span></span>

<span data-ttu-id="a7e78-111">無。</span><span class="sxs-lookup"><span data-stu-id="a7e78-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a7e78-112">子元素</span><span class="sxs-lookup"><span data-stu-id="a7e78-112">Child Elements</span></span>

<span data-ttu-id="a7e78-113">無。</span><span class="sxs-lookup"><span data-stu-id="a7e78-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a7e78-114">父元素</span><span class="sxs-lookup"><span data-stu-id="a7e78-114">Parent Elements</span></span>

|<span data-ttu-id="a7e78-115">元素</span><span class="sxs-lookup"><span data-stu-id="a7e78-115">Element</span></span>|<span data-ttu-id="a7e78-116">描述</span><span class="sxs-lookup"><span data-stu-id="a7e78-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a7e78-117">ItemSelectionCondition ListControl （格式） 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="a7e78-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="a7e78-118">定義要使用此清單項目必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="a7e78-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a7e78-119">文字值</span><span class="sxs-lookup"><span data-stu-id="a7e78-119">Text Value</span></span>

<span data-ttu-id="a7e78-120">指定評估指令碼。</span><span class="sxs-lookup"><span data-stu-id="a7e78-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="a7e78-121">備註</span><span class="sxs-lookup"><span data-stu-id="a7e78-121">Remarks</span></span>

<span data-ttu-id="a7e78-122">如果會使用這個項目，您不能指定`PropertyName`時定義的選取項目條件的項目。</span><span class="sxs-lookup"><span data-stu-id="a7e78-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7e78-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7e78-123">See Also</span></span>

[<span data-ttu-id="a7e78-124">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="a7e78-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
