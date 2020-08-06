---
title: GroupBy (格式的之 entryselectedby 的 TypeName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e62762cf142bd2d20b21ad8f4249285bd3679280
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780259"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="1ae33-102">GroupBy 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1ae33-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="1ae33-103">指定使用自訂控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="1ae33-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="1ae33-104">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="1ae33-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="1ae33-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素（GroupBy (格式）) CustomEntries 專案（適用于 CustomEntry 的 groupby (格式) CustomControl 專案 (格式) 之 entryselectedby 元素用於 groupby (格式的 CustomEntry) TypeName 元素 (</span><span class="sxs-lookup"><span data-stu-id="1ae33-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1ae33-106">語法</span><span class="sxs-lookup"><span data-stu-id="1ae33-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1ae33-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1ae33-107">Attributes and Elements</span></span>

<span data-ttu-id="1ae33-108">下列各節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="1ae33-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1ae33-109">屬性</span><span class="sxs-lookup"><span data-stu-id="1ae33-109">Attributes</span></span>

<span data-ttu-id="1ae33-110">無。</span><span class="sxs-lookup"><span data-stu-id="1ae33-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1ae33-111">子元素</span><span class="sxs-lookup"><span data-stu-id="1ae33-111">Child Elements</span></span>

<span data-ttu-id="1ae33-112">無。</span><span class="sxs-lookup"><span data-stu-id="1ae33-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1ae33-113">父項目</span><span class="sxs-lookup"><span data-stu-id="1ae33-113">Parent Elements</span></span>

|<span data-ttu-id="1ae33-114">元素</span><span class="sxs-lookup"><span data-stu-id="1ae33-114">Element</span></span>|<span data-ttu-id="1ae33-115">描述</span><span class="sxs-lookup"><span data-stu-id="1ae33-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1ae33-116">GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1ae33-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="1ae33-117">定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="1ae33-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1ae33-118">文字值</span><span class="sxs-lookup"><span data-stu-id="1ae33-118">Text Value</span></span>

<span data-ttu-id="1ae33-119">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。</span><span class="sxs-lookup"><span data-stu-id="1ae33-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ae33-120">備註</span><span class="sxs-lookup"><span data-stu-id="1ae33-120">Remarks</span></span>

<span data-ttu-id="1ae33-121">每個控制項定義都必須定義至少一個型別名稱、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="1ae33-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="1ae33-122">如需自訂控制項視圖之元件的詳細資訊，請參閱[建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="1ae33-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1ae33-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ae33-123">See Also</span></span>

[<span data-ttu-id="1ae33-124">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="1ae33-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="1ae33-125">GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1ae33-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="1ae33-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="1ae33-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
