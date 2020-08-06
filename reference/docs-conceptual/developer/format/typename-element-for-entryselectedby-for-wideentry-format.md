---
title: 之 entryselectedby for WideEntry (格式的 TypeName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9af443067467f590df824b28636f57b807a4fc94
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780180"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="5a3a5-102">WideEntry 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5a3a5-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="5a3a5-103">指定定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="5a3a5-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="5a3a5-104">每當顯示此物件時，就會使用此定義。</span><span class="sxs-lookup"><span data-stu-id="5a3a5-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="5a3a5-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 專案 (格式) WideEntries 專案 (格式) WideEntry 專案 (格式) 之 entryselectedby 元素用於 WideEntry (格式的) TypeName 元素 (</span><span class="sxs-lookup"><span data-stu-id="5a3a5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5a3a5-106">語法</span><span class="sxs-lookup"><span data-stu-id="5a3a5-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5a3a5-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5a3a5-107">Attributes and Elements</span></span>

<span data-ttu-id="5a3a5-108">下列各節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="5a3a5-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5a3a5-109">屬性</span><span class="sxs-lookup"><span data-stu-id="5a3a5-109">Attributes</span></span>

<span data-ttu-id="5a3a5-110">無。</span><span class="sxs-lookup"><span data-stu-id="5a3a5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5a3a5-111">子元素</span><span class="sxs-lookup"><span data-stu-id="5a3a5-111">Child Elements</span></span>

<span data-ttu-id="5a3a5-112">無。</span><span class="sxs-lookup"><span data-stu-id="5a3a5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5a3a5-113">父項目</span><span class="sxs-lookup"><span data-stu-id="5a3a5-113">Parent Elements</span></span>

|<span data-ttu-id="5a3a5-114">元素</span><span class="sxs-lookup"><span data-stu-id="5a3a5-114">Element</span></span>|<span data-ttu-id="5a3a5-115">描述</span><span class="sxs-lookup"><span data-stu-id="5a3a5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5a3a5-116">WideEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5a3a5-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="5a3a5-117">定義使用此寬專案的 .NET 類型，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="5a3a5-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5a3a5-118">文字值</span><span class="sxs-lookup"><span data-stu-id="5a3a5-118">Text Value</span></span>

<span data-ttu-id="5a3a5-119">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。</span><span class="sxs-lookup"><span data-stu-id="5a3a5-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="5a3a5-120">備註</span><span class="sxs-lookup"><span data-stu-id="5a3a5-120">Remarks</span></span>

<span data-ttu-id="5a3a5-121">每個寬型別都必須指定一個或多個 .NET 類型、一個選取集，或必須存在才能使用定義的選取條件。</span><span class="sxs-lookup"><span data-stu-id="5a3a5-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="5a3a5-122">如需有關寬視圖之其他元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="5a3a5-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5a3a5-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a3a5-123">See Also</span></span>

[<span data-ttu-id="5a3a5-124">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="5a3a5-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="5a3a5-125">WideEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5a3a5-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="5a3a5-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="5a3a5-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
