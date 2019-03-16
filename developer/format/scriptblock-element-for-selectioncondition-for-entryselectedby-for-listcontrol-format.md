---
title: 針對 ListControl （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: b65d953169f6daf15fb617ce4d0303cf4cb584ee
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057768"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="a9cef-102">ListControl 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a9cef-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="a9cef-103">指定的指令碼，就會觸發條件。</span><span class="sxs-lookup"><span data-stu-id="a9cef-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="a9cef-104">此指令碼會評估為`true`、 符合條件，和使用清單項目。</span><span class="sxs-lookup"><span data-stu-id="a9cef-104">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="a9cef-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 （格式） ListEntry 項目 （格式） EntrySelectedBy 項目用於 ListEntry （格式） SelectionCondition 元素EntrySelectedBy ListEntry （格式） 的 EntrySelectedBy 的 SelectionCondition ListEntry （格式） ScriptBlock 元素</span><span class="sxs-lookup"><span data-stu-id="a9cef-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a9cef-106">語法</span><span class="sxs-lookup"><span data-stu-id="a9cef-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a9cef-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="a9cef-107">Attributes and Elements</span></span>

<span data-ttu-id="a9cef-108">下列各節說明屬性、 子項目和父項目`ScriptBlock`項目。</span><span class="sxs-lookup"><span data-stu-id="a9cef-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a9cef-109">屬性</span><span class="sxs-lookup"><span data-stu-id="a9cef-109">Attributes</span></span>

<span data-ttu-id="a9cef-110">無。</span><span class="sxs-lookup"><span data-stu-id="a9cef-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a9cef-111">子元素</span><span class="sxs-lookup"><span data-stu-id="a9cef-111">Child Elements</span></span>

<span data-ttu-id="a9cef-112">無。</span><span class="sxs-lookup"><span data-stu-id="a9cef-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a9cef-113">父元素</span><span class="sxs-lookup"><span data-stu-id="a9cef-113">Parent Elements</span></span>

|<span data-ttu-id="a9cef-114">元素</span><span class="sxs-lookup"><span data-stu-id="a9cef-114">Element</span></span>|<span data-ttu-id="a9cef-115">描述</span><span class="sxs-lookup"><span data-stu-id="a9cef-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a9cef-116">ListEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="a9cef-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="a9cef-117">定義要使用此清單項目必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="a9cef-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a9cef-118">文字值</span><span class="sxs-lookup"><span data-stu-id="a9cef-118">Text Value</span></span>

<span data-ttu-id="a9cef-119">指定評估指令碼。</span><span class="sxs-lookup"><span data-stu-id="a9cef-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="a9cef-120">備註</span><span class="sxs-lookup"><span data-stu-id="a9cef-120">Remarks</span></span>

<span data-ttu-id="a9cef-121">選取條件必須指定至少一個指令碼或屬性名稱來評估，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="a9cef-121">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="a9cef-122">(如需如何使用選擇條件的詳細資訊，請參閱[定義條件時檢視項目或項目用](./defining-conditions-for-displaying-data.md)。)</span><span class="sxs-lookup"><span data-stu-id="a9cef-122">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="a9cef-123">清單檢視的其他元件的相關資訊，請參閱[清單檢視](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="a9cef-123">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a9cef-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9cef-124">See Also</span></span>

[<span data-ttu-id="a9cef-125">ListEntry 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="a9cef-125">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="a9cef-126">PropertyName ListEntry （格式） 的 EntrySelectedBy 的 SelectionCondition 的項目</span><span class="sxs-lookup"><span data-stu-id="a9cef-126">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="a9cef-127">ListEntry （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="a9cef-127">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="a9cef-128">清單檢視</span><span class="sxs-lookup"><span data-stu-id="a9cef-128">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="a9cef-129">使用 檢視項目或項目時定義的條件</span><span class="sxs-lookup"><span data-stu-id="a9cef-129">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a9cef-130">撰寫 Windows PowerShell 格式和類型的檔案</span><span class="sxs-lookup"><span data-stu-id="a9cef-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
