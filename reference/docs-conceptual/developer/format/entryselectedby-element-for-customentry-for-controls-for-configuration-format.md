---
title: 設定之控制項的 CustomEntry 的之 entryselectedby 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368767"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="c3af6-102">設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c3af6-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="c3af6-103">定義使用通用控制項定義的 .NET 類型，或必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="c3af6-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="c3af6-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="c3af6-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="c3af6-105">Configuration 元素（格式）控制設定（format） CustomControl 元素的設定（格式）控制項專案的設定專案（格式） CustomControl 設定的 CustomEntries 元素（格式）Format） CustomEntry 元素，用於 CustomControl 控制項的設定（格式）之 entryselectedby 元素（用於設定的控制項）（格式）</span><span class="sxs-lookup"><span data-stu-id="c3af6-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c3af6-106">語法</span><span class="sxs-lookup"><span data-stu-id="c3af6-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c3af6-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="c3af6-107">Attributes and Elements</span></span>

<span data-ttu-id="c3af6-108">下列各節說明屬性、子專案，以及 `EntrySelectedBy` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="c3af6-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c3af6-109">屬性</span><span class="sxs-lookup"><span data-stu-id="c3af6-109">Attributes</span></span>

<span data-ttu-id="c3af6-110">無。</span><span class="sxs-lookup"><span data-stu-id="c3af6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c3af6-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c3af6-111">Child Elements</span></span>

|<span data-ttu-id="c3af6-112">元素</span><span class="sxs-lookup"><span data-stu-id="c3af6-112">Element</span></span>|<span data-ttu-id="c3af6-113">描述</span><span class="sxs-lookup"><span data-stu-id="c3af6-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c3af6-114">設定之控制項的之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c3af6-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="c3af6-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="c3af6-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c3af6-116">定義必須存在的條件，才能使用通用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="c3af6-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="c3af6-117">設定之控制項的之 entryselectedby 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c3af6-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="c3af6-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="c3af6-118">Optional element.</span></span><br /><br /> <span data-ttu-id="c3af6-119">指定一組使用此通用控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="c3af6-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="c3af6-120">設定之控制項的之 entryselectedby 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c3af6-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="c3af6-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="c3af6-121">Optional element.</span></span><br /><br /> <span data-ttu-id="c3af6-122">指定使用此通用控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="c3af6-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c3af6-123">父元素</span><span class="sxs-lookup"><span data-stu-id="c3af6-123">Parent Elements</span></span>

|<span data-ttu-id="c3af6-124">元素</span><span class="sxs-lookup"><span data-stu-id="c3af6-124">Element</span></span>|<span data-ttu-id="c3af6-125">描述</span><span class="sxs-lookup"><span data-stu-id="c3af6-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c3af6-126">設定之控制項的 CustomControl 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c3af6-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="c3af6-127">提供通用控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="c3af6-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c3af6-128">備註</span><span class="sxs-lookup"><span data-stu-id="c3af6-128">Remarks</span></span>

<span data-ttu-id="c3af6-129">每個定義至少必須指定一個 .NET 類型、選取範圍或選取條件。</span><span class="sxs-lookup"><span data-stu-id="c3af6-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="c3af6-130">您可以指定的類型、選擇集或選取條件的數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="c3af6-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3af6-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3af6-131">See Also</span></span>

[<span data-ttu-id="c3af6-132">設定之控制項的之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c3af6-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="c3af6-133">設定之控制項的之 entryselectedby 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c3af6-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="c3af6-134">設定之控制項的 CustomControl 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c3af6-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="c3af6-135">設定之控制項的之 entryselectedby 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c3af6-135">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="c3af6-136">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="c3af6-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
