---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之 SelectionCondition 的 TypeName 元素 (格式)
description: GroupBy 之 SelectionCondition 的 TypeName 元素 (格式)
ms.openlocfilehash: 096d2355e113a7e44cc6ae31ea23efc3f01080a0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664632"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="c6975-103">GroupBy 之 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c6975-103">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="c6975-104">指定觸發條件的 .NET 型別。</span><span class="sxs-lookup"><span data-stu-id="c6975-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="c6975-105">定義如何顯示新的物件群組時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="c6975-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="c6975-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 專案的視圖 (格式) CustomEntries 元素用於 GroupBy (格式) 元素用於 CustomEntry 的 groupby (格式) CustomControl 專案用於之 entryselectedby 的 groupby (格式) 專案的 CustomEntry 專案 (格式)  (格式的 SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="c6975-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c6975-107">語法</span><span class="sxs-lookup"><span data-stu-id="c6975-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c6975-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c6975-108">Attributes and Elements</span></span>

<span data-ttu-id="c6975-109">下列各節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="c6975-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c6975-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c6975-110">Attributes</span></span>

<span data-ttu-id="c6975-111">無。</span><span class="sxs-lookup"><span data-stu-id="c6975-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c6975-112">子元素</span><span class="sxs-lookup"><span data-stu-id="c6975-112">Child Elements</span></span>

<span data-ttu-id="c6975-113">無。</span><span class="sxs-lookup"><span data-stu-id="c6975-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c6975-114">父項目</span><span class="sxs-lookup"><span data-stu-id="c6975-114">Parent Elements</span></span>

|<span data-ttu-id="c6975-115">元素</span><span class="sxs-lookup"><span data-stu-id="c6975-115">Element</span></span>|<span data-ttu-id="c6975-116">描述</span><span class="sxs-lookup"><span data-stu-id="c6975-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c6975-117">GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c6975-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="c6975-118">定義必須存在才能使用控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="c6975-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c6975-119">文字值</span><span class="sxs-lookup"><span data-stu-id="c6975-119">Text Value</span></span>

<span data-ttu-id="c6975-120">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。</span><span class="sxs-lookup"><span data-stu-id="c6975-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="c6975-121">備註</span><span class="sxs-lookup"><span data-stu-id="c6975-121">Remarks</span></span>

<span data-ttu-id="c6975-122">當指定這個專案時，您不能指定此 `SelectionSetName` 元素。</span><span class="sxs-lookup"><span data-stu-id="c6975-122">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="c6975-123">如需定義選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c6975-123">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c6975-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6975-124">See Also</span></span>

[<span data-ttu-id="c6975-125">GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c6975-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="c6975-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="c6975-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
