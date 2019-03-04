---
title: SelectionSetName EntrySelectedBy 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860904"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="cbf54-102">設定之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="cbf54-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="cbf54-103">指定一組使用這個控制項定義的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="cbf54-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="cbf54-104">定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="cbf54-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="cbf54-105">組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目CustomControl CustomEntry EntrySelectedBy 控制項組態 （格式） 的組態 （格式） SelectionSetName 元素的控制項的組態 （格式） EntrySelectedBy 元素的控制項的格式） CustomEntry 項目</span><span class="sxs-lookup"><span data-stu-id="cbf54-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cbf54-106">語法</span><span class="sxs-lookup"><span data-stu-id="cbf54-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="cbf54-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="cbf54-107">Attributes and Elements</span></span>

<span data-ttu-id="cbf54-108">下列各節說明屬性、 子項目和父項目`SelectionSetName`項目。</span><span class="sxs-lookup"><span data-stu-id="cbf54-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cbf54-109">屬性</span><span class="sxs-lookup"><span data-stu-id="cbf54-109">Attributes</span></span>

<span data-ttu-id="cbf54-110">無</span><span class="sxs-lookup"><span data-stu-id="cbf54-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="cbf54-111">子元素</span><span class="sxs-lookup"><span data-stu-id="cbf54-111">Child Elements</span></span>

<span data-ttu-id="cbf54-112">無。</span><span class="sxs-lookup"><span data-stu-id="cbf54-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cbf54-113">父元素</span><span class="sxs-lookup"><span data-stu-id="cbf54-113">Parent Elements</span></span>

|<span data-ttu-id="cbf54-114">元素</span><span class="sxs-lookup"><span data-stu-id="cbf54-114">Element</span></span>|<span data-ttu-id="cbf54-115">描述</span><span class="sxs-lookup"><span data-stu-id="cbf54-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cbf54-116">EntrySelectedBy CustomEntry 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="cbf54-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="cbf54-117">定義使用此控制項定義或必須存在於要使用此定義條件的.NET 類型。</span><span class="sxs-lookup"><span data-stu-id="cbf54-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cbf54-118">文字值</span><span class="sxs-lookup"><span data-stu-id="cbf54-118">Text Value</span></span>

<span data-ttu-id="cbf54-119">指定選取項目集的名稱。</span><span class="sxs-lookup"><span data-stu-id="cbf54-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="cbf54-120">備註</span><span class="sxs-lookup"><span data-stu-id="cbf54-120">Remarks</span></span>

<span data-ttu-id="cbf54-121">每個控制項定義必須至少一個型別名稱、 選取項目集或選擇條件的定義。</span><span class="sxs-lookup"><span data-stu-id="cbf54-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="cbf54-122">您想要在多個檢視中定義一組所使用的物件時，會通常會使用選取項目集。</span><span class="sxs-lookup"><span data-stu-id="cbf54-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="cbf54-123">如需定義選取項目集的詳細資訊，請參閱[定義的選取項目設定](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="cbf54-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cbf54-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbf54-124">See Also</span></span>

[<span data-ttu-id="cbf54-125">EntrySelectedBy CustomEntry 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="cbf54-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="cbf54-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="cbf54-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
