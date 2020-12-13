---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之 EntrySelectedBy 的 TypeName 元素 (格式)
description: GroupBy 之 EntrySelectedBy 的 TypeName 元素 (格式)
ms.openlocfilehash: 07cc92e9c501aa0eb2d219e416851be0fcd80f47
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645713"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="12d3f-103">GroupBy 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="12d3f-103">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="12d3f-104">指定使用此自訂控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="12d3f-104">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="12d3f-105">定義如何顯示新的物件群組時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="12d3f-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="12d3f-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 專案的視圖 (格式) CustomEntries 元素適用于 GroupBy (格式) 元素用於 CustomEntry 的 groupby (格式) 元素用於 CustomControl 的 groupby (格式)  (的之 entryselectedby 專案) 格式 (</span><span class="sxs-lookup"><span data-stu-id="12d3f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="12d3f-107">語法</span><span class="sxs-lookup"><span data-stu-id="12d3f-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="12d3f-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="12d3f-108">Attributes and Elements</span></span>

<span data-ttu-id="12d3f-109">下列各節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="12d3f-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="12d3f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="12d3f-110">Attributes</span></span>

<span data-ttu-id="12d3f-111">無。</span><span class="sxs-lookup"><span data-stu-id="12d3f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="12d3f-112">子元素</span><span class="sxs-lookup"><span data-stu-id="12d3f-112">Child Elements</span></span>

<span data-ttu-id="12d3f-113">無。</span><span class="sxs-lookup"><span data-stu-id="12d3f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="12d3f-114">父項目</span><span class="sxs-lookup"><span data-stu-id="12d3f-114">Parent Elements</span></span>

|<span data-ttu-id="12d3f-115">元素</span><span class="sxs-lookup"><span data-stu-id="12d3f-115">Element</span></span>|<span data-ttu-id="12d3f-116">描述</span><span class="sxs-lookup"><span data-stu-id="12d3f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="12d3f-117">GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="12d3f-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="12d3f-118">定義使用此控制項定義的 .NET 型別，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="12d3f-118">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="12d3f-119">文字值</span><span class="sxs-lookup"><span data-stu-id="12d3f-119">Text Value</span></span>

<span data-ttu-id="12d3f-120">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。</span><span class="sxs-lookup"><span data-stu-id="12d3f-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="12d3f-121">備註</span><span class="sxs-lookup"><span data-stu-id="12d3f-121">Remarks</span></span>

<span data-ttu-id="12d3f-122">每個控制項定義都必須定義至少一個類型名稱、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="12d3f-122">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="12d3f-123">如需自訂控制項視圖元件的詳細資訊，請參閱 [建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="12d3f-123">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="12d3f-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12d3f-124">See Also</span></span>

[<span data-ttu-id="12d3f-125">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="12d3f-125">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="12d3f-126">GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="12d3f-126">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="12d3f-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="12d3f-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
