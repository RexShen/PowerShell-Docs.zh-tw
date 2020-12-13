---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 SelectionCondition 的 TypeName 元素 (格式)
description: 設定之控制項的 SelectionCondition 的 TypeName 元素 (格式)
ms.openlocfilehash: fddb8ddbac7c9292a05cadfa31f98db6439a557d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659672"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="9a63f-103">設定之控制項的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9a63f-103">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="9a63f-104">指定觸發條件的 .NET 型別。</span><span class="sxs-lookup"><span data-stu-id="9a63f-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="9a63f-105">當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="9a63f-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="9a63f-106">設定元素 (格式) 控制項的設定專案 (格式) 控制項的控制項專案 (格式) CustomEntry 專案的設定 (格式控制項的 CustomControl) 格式 (針對 configuration (格式的控制項的 CustomControl 格式) 之 entryselectedby 元素，用於 CustomEntry 的控制項設定 (格式) SelectionCondition 專案（之 entryselectedby for CustomEntry for SelectionCondition for for configuration (格式）) </span><span class="sxs-lookup"><span data-stu-id="9a63f-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9a63f-107">語法</span><span class="sxs-lookup"><span data-stu-id="9a63f-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="9a63f-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9a63f-108">Attributes and Elements</span></span>

<span data-ttu-id="9a63f-109">下列各節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="9a63f-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9a63f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="9a63f-110">Attributes</span></span>

<span data-ttu-id="9a63f-111">無。</span><span class="sxs-lookup"><span data-stu-id="9a63f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9a63f-112">子元素</span><span class="sxs-lookup"><span data-stu-id="9a63f-112">Child Elements</span></span>

<span data-ttu-id="9a63f-113">無。</span><span class="sxs-lookup"><span data-stu-id="9a63f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9a63f-114">父項目</span><span class="sxs-lookup"><span data-stu-id="9a63f-114">Parent Elements</span></span>

|<span data-ttu-id="9a63f-115">元素</span><span class="sxs-lookup"><span data-stu-id="9a63f-115">Element</span></span>|<span data-ttu-id="9a63f-116">描述</span><span class="sxs-lookup"><span data-stu-id="9a63f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9a63f-117">適用于 CustomEntry 之之 entryselectedby 的 SelectionCondition 元素 (格式設定格式) </span><span class="sxs-lookup"><span data-stu-id="9a63f-117">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="9a63f-118">定義必須存在才能使用控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="9a63f-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9a63f-119">文字值</span><span class="sxs-lookup"><span data-stu-id="9a63f-119">Text Value</span></span>

<span data-ttu-id="9a63f-120">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。</span><span class="sxs-lookup"><span data-stu-id="9a63f-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="9a63f-121">備註</span><span class="sxs-lookup"><span data-stu-id="9a63f-121">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="9a63f-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a63f-122">See Also</span></span>

[<span data-ttu-id="9a63f-123">適用于 CustomEntry 之之 entryselectedby 的 SelectionCondition 元素 (格式設定格式) </span><span class="sxs-lookup"><span data-stu-id="9a63f-123">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="9a63f-124">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="9a63f-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
