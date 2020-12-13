---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 EntrySelectedBy 的 TypeName 元素 (格式)
description: 設定之控制項的 EntrySelectedBy 的 TypeName 元素 (格式)
ms.openlocfilehash: ce74c23ca35597902c6b94fdccd44324ba8e0233
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667737"
---
# <a name="typename-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="3248c-103">設定之控制項的 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3248c-103">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="3248c-104">指定使用此控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="3248c-104">Specifies a .NET type that uses this definition of the control.</span></span> <span data-ttu-id="3248c-105">當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="3248c-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="3248c-106">設定專案 (格式) 控制項設定的控制項專案 (格式設定的控制項) 控制項專案 (格式) CustomEntries 專案的 CustomControl 設定 (格式) 的格式 (格式) 的格式 (格式)  (格式控制項的控制項) 格式 (的控制項的 CustomControl 的控制項) 格式</span><span class="sxs-lookup"><span data-stu-id="3248c-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3248c-107">語法</span><span class="sxs-lookup"><span data-stu-id="3248c-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="3248c-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3248c-108">Attributes and Elements</span></span>

<span data-ttu-id="3248c-109">下列各節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="3248c-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3248c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="3248c-110">Attributes</span></span>

<span data-ttu-id="3248c-111">無。</span><span class="sxs-lookup"><span data-stu-id="3248c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3248c-112">子元素</span><span class="sxs-lookup"><span data-stu-id="3248c-112">Child Elements</span></span>

<span data-ttu-id="3248c-113">無。</span><span class="sxs-lookup"><span data-stu-id="3248c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3248c-114">父項目</span><span class="sxs-lookup"><span data-stu-id="3248c-114">Parent Elements</span></span>

|<span data-ttu-id="3248c-115">元素</span><span class="sxs-lookup"><span data-stu-id="3248c-115">Element</span></span>|<span data-ttu-id="3248c-116">描述</span><span class="sxs-lookup"><span data-stu-id="3248c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3248c-117">設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3248c-117">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="3248c-118">定義使用此控制項定義的 .NET 型別，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="3248c-118">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3248c-119">文字值</span><span class="sxs-lookup"><span data-stu-id="3248c-119">Text Value</span></span>

<span data-ttu-id="3248c-120">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。</span><span class="sxs-lookup"><span data-stu-id="3248c-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="3248c-121">備註</span><span class="sxs-lookup"><span data-stu-id="3248c-121">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="3248c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3248c-122">See Also</span></span>

[<span data-ttu-id="3248c-123">設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="3248c-123">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="3248c-124">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="3248c-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
