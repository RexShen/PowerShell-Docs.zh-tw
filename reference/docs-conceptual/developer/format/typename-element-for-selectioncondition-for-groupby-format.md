---
title: GroupBy 的 SelectionCondition 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361477"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="4703d-102">GroupBy 之 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4703d-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="4703d-103">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="4703d-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="4703d-104">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="4703d-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="4703d-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（format） CustomEntries 專案的 groupby （format） CustomControl 元素，適用于的 CustomControl for GroupBy （format） CustomEntry 元素適用于 CustomEntry 之 groupby （format） SelectionCondition 元素的 GroupBy （format）之 entryselectedby 元素的 CustomControl，適用于之 entryselectedby 的 groupby （格式）</span><span class="sxs-lookup"><span data-stu-id="4703d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4703d-106">語法</span><span class="sxs-lookup"><span data-stu-id="4703d-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="4703d-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="4703d-107">Attributes and Elements</span></span>

<span data-ttu-id="4703d-108">下列各節說明屬性、子專案，以及 `TypeName` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="4703d-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4703d-109">屬性</span><span class="sxs-lookup"><span data-stu-id="4703d-109">Attributes</span></span>

<span data-ttu-id="4703d-110">無。</span><span class="sxs-lookup"><span data-stu-id="4703d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4703d-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4703d-111">Child Elements</span></span>

<span data-ttu-id="4703d-112">無。</span><span class="sxs-lookup"><span data-stu-id="4703d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4703d-113">父元素</span><span class="sxs-lookup"><span data-stu-id="4703d-113">Parent Elements</span></span>

|<span data-ttu-id="4703d-114">元素</span><span class="sxs-lookup"><span data-stu-id="4703d-114">Element</span></span>|<span data-ttu-id="4703d-115">描述</span><span class="sxs-lookup"><span data-stu-id="4703d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4703d-116">GroupBy 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4703d-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="4703d-117">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="4703d-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4703d-118">文字值</span><span class="sxs-lookup"><span data-stu-id="4703d-118">Text Value</span></span>

<span data-ttu-id="4703d-119">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="4703d-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="4703d-120">備註</span><span class="sxs-lookup"><span data-stu-id="4703d-120">Remarks</span></span>

<span data-ttu-id="4703d-121">當指定這個元素時，您無法指定 `SelectionSetName` 元素。</span><span class="sxs-lookup"><span data-stu-id="4703d-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="4703d-122">如需定義選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="4703d-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4703d-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4703d-123">See Also</span></span>

[<span data-ttu-id="4703d-124">GroupBy 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4703d-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="4703d-125">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="4703d-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
