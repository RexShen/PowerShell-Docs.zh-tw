---
title: 控制項的之 entryselectedby 的 TypeName 元素，用於 View (Format) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6eaa4f80a18c91ca351657fd40a8cac6f688c22f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783325"
---
# <a name="typename-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="a5a78-102">檢視之控制項的 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a5a78-102">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="a5a78-103">指定使用此控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="a5a78-103">Specifies a .NET type that uses this definition of the control.</span></span> <span data-ttu-id="a5a78-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="a5a78-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="a5a78-105">Configuration 專案 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 CustomControl 格式 CustomEntries 的控制項 (格式控制項) CustomControl 元素 CustomEntry 的控制項視圖 (格式) CustomEntries 元素之 entryselectedby 的控制項 (格式) 的專案的專案</span><span class="sxs-lookup"><span data-stu-id="a5a78-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a5a78-106">語法</span><span class="sxs-lookup"><span data-stu-id="a5a78-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="a5a78-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a5a78-107">Attributes and Elements</span></span>

<span data-ttu-id="a5a78-108">下列各節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="a5a78-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a5a78-109">屬性</span><span class="sxs-lookup"><span data-stu-id="a5a78-109">Attributes</span></span>

<span data-ttu-id="a5a78-110">無。</span><span class="sxs-lookup"><span data-stu-id="a5a78-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a5a78-111">子元素</span><span class="sxs-lookup"><span data-stu-id="a5a78-111">Child Elements</span></span>

<span data-ttu-id="a5a78-112">無。</span><span class="sxs-lookup"><span data-stu-id="a5a78-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a5a78-113">父項目</span><span class="sxs-lookup"><span data-stu-id="a5a78-113">Parent Elements</span></span>

|<span data-ttu-id="a5a78-114">元素</span><span class="sxs-lookup"><span data-stu-id="a5a78-114">Element</span></span>|<span data-ttu-id="a5a78-115">描述</span><span class="sxs-lookup"><span data-stu-id="a5a78-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a5a78-116">檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a5a78-116">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="a5a78-117">定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="a5a78-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a5a78-118">文字值</span><span class="sxs-lookup"><span data-stu-id="a5a78-118">Text Value</span></span>

<span data-ttu-id="a5a78-119">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。</span><span class="sxs-lookup"><span data-stu-id="a5a78-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="a5a78-120">備註</span><span class="sxs-lookup"><span data-stu-id="a5a78-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="a5a78-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5a78-121">See Also</span></span>

[<span data-ttu-id="a5a78-122">檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a5a78-122">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="a5a78-123">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="a5a78-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
