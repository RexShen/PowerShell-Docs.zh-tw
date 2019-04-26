---
title: GroupBy （格式） 的 SelectionCondition TypeName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083768"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="be437-102">GroupBy 之 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="be437-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="be437-103">指定觸發條件的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="be437-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="be437-104">定義新的群組物件的顯示方式時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="be437-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="be437-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素CustomControl CustomEntry EntrySelectedBy SelectionCondition 的 GroupBy （格式） 的 GroupBy （格式） 類型名稱元素的 GroupBy （格式） SelectionCondition 元素的 GroupBy （格式） EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="be437-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="be437-106">語法</span><span class="sxs-lookup"><span data-stu-id="be437-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="be437-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="be437-107">Attributes and Elements</span></span>

<span data-ttu-id="be437-108">下列各節說明屬性、 子項目和父項目`TypeName`項目。</span><span class="sxs-lookup"><span data-stu-id="be437-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="be437-109">屬性</span><span class="sxs-lookup"><span data-stu-id="be437-109">Attributes</span></span>

<span data-ttu-id="be437-110">無。</span><span class="sxs-lookup"><span data-stu-id="be437-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="be437-111">子元素</span><span class="sxs-lookup"><span data-stu-id="be437-111">Child Elements</span></span>

<span data-ttu-id="be437-112">無。</span><span class="sxs-lookup"><span data-stu-id="be437-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="be437-113">父項目</span><span class="sxs-lookup"><span data-stu-id="be437-113">Parent Elements</span></span>

|<span data-ttu-id="be437-114">項目</span><span class="sxs-lookup"><span data-stu-id="be437-114">Element</span></span>|<span data-ttu-id="be437-115">描述</span><span class="sxs-lookup"><span data-stu-id="be437-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="be437-116">GroupBy （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="be437-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="be437-117">定義必須存在，要使用的控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="be437-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="be437-118">文字值</span><span class="sxs-lookup"><span data-stu-id="be437-118">Text Value</span></span>

<span data-ttu-id="be437-119">指定完整的.NET 型別名稱，例如`System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="be437-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="be437-120">備註</span><span class="sxs-lookup"><span data-stu-id="be437-120">Remarks</span></span>

<span data-ttu-id="be437-121">當指定這個項目時，您無法指定`SelectionSetName`項目。</span><span class="sxs-lookup"><span data-stu-id="be437-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="be437-122">如需定義選擇條件的詳細資訊，請參閱 <<c0> [ 定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="be437-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="be437-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be437-123">See Also</span></span>

[<span data-ttu-id="be437-124">GroupBy （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="be437-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="be437-125">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="be437-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
