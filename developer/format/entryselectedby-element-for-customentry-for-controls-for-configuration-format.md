---
title: EntrySelectedBy CustomEntry 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059213"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="29e9a-102">設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="29e9a-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="29e9a-103">定義使用的通用控制項或條件必須存在於要使用這個控制項定義的.NET 類型。</span><span class="sxs-lookup"><span data-stu-id="29e9a-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="29e9a-104">定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="29e9a-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="29e9a-105">組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目CustomControl CustomEntry 控制項組態 （格式） 的組態 （格式） EntrySelectedBy 元素的控制項的格式） CustomEntry 項目</span><span class="sxs-lookup"><span data-stu-id="29e9a-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="29e9a-106">語法</span><span class="sxs-lookup"><span data-stu-id="29e9a-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="29e9a-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="29e9a-107">Attributes and Elements</span></span>

<span data-ttu-id="29e9a-108">下列各節說明屬性、 子項目和父項目`EntrySelectedBy`項目。</span><span class="sxs-lookup"><span data-stu-id="29e9a-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="29e9a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="29e9a-109">Attributes</span></span>

<span data-ttu-id="29e9a-110">無。</span><span class="sxs-lookup"><span data-stu-id="29e9a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="29e9a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="29e9a-111">Child Elements</span></span>

|<span data-ttu-id="29e9a-112">元素</span><span class="sxs-lookup"><span data-stu-id="29e9a-112">Element</span></span>|<span data-ttu-id="29e9a-113">描述</span><span class="sxs-lookup"><span data-stu-id="29e9a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="29e9a-114">SelectionCondition EntrySelectedBy 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="29e9a-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="29e9a-115">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="29e9a-115">Optional element.</span></span><br /><br /> <span data-ttu-id="29e9a-116">定義必須存在通用控制項定義要使用的條件。</span><span class="sxs-lookup"><span data-stu-id="29e9a-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="29e9a-117">SelectionSetName EntrySelectedBy 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="29e9a-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="29e9a-118">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="29e9a-118">Optional element.</span></span><br /><br /> <span data-ttu-id="29e9a-119">指定一組使用通用控制項的這個定義的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="29e9a-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="29e9a-120">TypeName EntrySelectedBy 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="29e9a-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="29e9a-121">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="29e9a-121">Optional element.</span></span><br /><br /> <span data-ttu-id="29e9a-122">指定會使用通用控制項的這個定義的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="29e9a-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="29e9a-123">父元素</span><span class="sxs-lookup"><span data-stu-id="29e9a-123">Parent Elements</span></span>

|<span data-ttu-id="29e9a-124">元素</span><span class="sxs-lookup"><span data-stu-id="29e9a-124">Element</span></span>|<span data-ttu-id="29e9a-125">描述</span><span class="sxs-lookup"><span data-stu-id="29e9a-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="29e9a-126">CustomEntry CustomControl 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="29e9a-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="29e9a-127">提供通用控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="29e9a-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="29e9a-128">備註</span><span class="sxs-lookup"><span data-stu-id="29e9a-128">Remarks</span></span>

<span data-ttu-id="29e9a-129">最小值，每個定義必須至少一個.NET 類型、 選取項目集或指定的選取範圍條件。</span><span class="sxs-lookup"><span data-stu-id="29e9a-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="29e9a-130">沒有任何類型、 選取項目集或選擇條件，您可以指定數目的最大限制。</span><span class="sxs-lookup"><span data-stu-id="29e9a-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="29e9a-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29e9a-131">See Also</span></span>

[<span data-ttu-id="29e9a-132">SelectionCondition EntrySelectedBy 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="29e9a-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="29e9a-133">SelectionSetName EntrySelectedBy 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="29e9a-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="29e9a-134">CustomEntry CustomControl 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="29e9a-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="29e9a-135">TypeName EntrySelectedBy 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="29e9a-135">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="29e9a-136">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="29e9a-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
