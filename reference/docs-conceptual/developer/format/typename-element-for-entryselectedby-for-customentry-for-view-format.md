---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之 CustomEntry 的 EntrySelectedBy 的 TypeName 元素 (格式)
description: 檢視之 CustomEntry 的 EntrySelectedBy 的 TypeName 元素 (格式)
ms.openlocfilehash: 72bb88bccc2bbd62f7ed160b820cf9169cb69341
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645743"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="d9477-103">檢視之 CustomEntry 的 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d9477-103">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="d9477-104">指定使用自訂控制項視圖之定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="d9477-104">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="d9477-105">可以針對定義指定的類型數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="d9477-105">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="d9477-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) CustomControl 專案 (格式) CustomEntries 專案 (格式) 元素 (格式) CustomEntry 專案 (格式) CustomEntries 專案之 entryselectedby for view (格式) CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="d9477-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d9477-107">語法</span><span class="sxs-lookup"><span data-stu-id="d9477-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d9477-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d9477-108">Attributes and Elements</span></span>

<span data-ttu-id="d9477-109">下列各節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="d9477-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d9477-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d9477-110">Attributes</span></span>

<span data-ttu-id="d9477-111">無。</span><span class="sxs-lookup"><span data-stu-id="d9477-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d9477-112">子元素</span><span class="sxs-lookup"><span data-stu-id="d9477-112">Child Elements</span></span>

<span data-ttu-id="d9477-113">無。</span><span class="sxs-lookup"><span data-stu-id="d9477-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d9477-114">父項目</span><span class="sxs-lookup"><span data-stu-id="d9477-114">Parent Elements</span></span>

|<span data-ttu-id="d9477-115">元素</span><span class="sxs-lookup"><span data-stu-id="d9477-115">Element</span></span>|<span data-ttu-id="d9477-116">描述</span><span class="sxs-lookup"><span data-stu-id="d9477-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d9477-117">適用于 CustomEntry 的之 entryselectedby 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="d9477-117">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="d9477-118">定義使用此自訂控制項視圖定義或必須存在的條件，以使用此定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="d9477-118">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d9477-119">文字值</span><span class="sxs-lookup"><span data-stu-id="d9477-119">Text Value</span></span>

<span data-ttu-id="d9477-120">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。</span><span class="sxs-lookup"><span data-stu-id="d9477-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="d9477-121">備註</span><span class="sxs-lookup"><span data-stu-id="d9477-121">Remarks</span></span>

<span data-ttu-id="d9477-122">每個自訂控制項視圖定義都必須定義至少一個類型名稱、選取集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="d9477-122">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="d9477-123">如需自訂控制項視圖元件的詳細資訊，請參閱 [建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="d9477-123">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d9477-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9477-124">See Also</span></span>

[<span data-ttu-id="d9477-125">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="d9477-125">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="d9477-126">適用于 CustomEntry 的之 entryselectedby 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="d9477-126">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d9477-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="d9477-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
