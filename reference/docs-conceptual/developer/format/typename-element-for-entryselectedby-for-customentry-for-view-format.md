---
title: CustomEntry for View 的之 entryselectedby 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368067"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="dc78d-102">檢視之 CustomEntry 的 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dc78d-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="dc78d-103">指定使用自訂控制項視圖之定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="dc78d-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="dc78d-104">可以針對定義指定的類型數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="dc78d-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="dc78d-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素（format） CustomEntries 元素，適用于 CustomEntry for View 的 CustomControl for View （format） CustomEntries 元素（格式）之 entryselectedbyCustomEntry for View （Format） TypeName 元素的元素，用於 CustomEntry for View 的之 entryselectedby （格式）</span><span class="sxs-lookup"><span data-stu-id="dc78d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dc78d-106">語法</span><span class="sxs-lookup"><span data-stu-id="dc78d-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dc78d-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="dc78d-107">Attributes and Elements</span></span>

<span data-ttu-id="dc78d-108">下列各節說明屬性、子專案，以及 `TypeName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="dc78d-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dc78d-109">屬性</span><span class="sxs-lookup"><span data-stu-id="dc78d-109">Attributes</span></span>

<span data-ttu-id="dc78d-110">無。</span><span class="sxs-lookup"><span data-stu-id="dc78d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dc78d-111">子元素</span><span class="sxs-lookup"><span data-stu-id="dc78d-111">Child Elements</span></span>

<span data-ttu-id="dc78d-112">無。</span><span class="sxs-lookup"><span data-stu-id="dc78d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dc78d-113">父元素</span><span class="sxs-lookup"><span data-stu-id="dc78d-113">Parent Elements</span></span>

|<span data-ttu-id="dc78d-114">元素</span><span class="sxs-lookup"><span data-stu-id="dc78d-114">Element</span></span>|<span data-ttu-id="dc78d-115">描述</span><span class="sxs-lookup"><span data-stu-id="dc78d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dc78d-116">CustomEntry for View 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="dc78d-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="dc78d-117">定義使用此自訂控制項視圖定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="dc78d-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dc78d-118">文字值</span><span class="sxs-lookup"><span data-stu-id="dc78d-118">Text Value</span></span>

<span data-ttu-id="dc78d-119">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="dc78d-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="dc78d-120">備註</span><span class="sxs-lookup"><span data-stu-id="dc78d-120">Remarks</span></span>

<span data-ttu-id="dc78d-121">每個自訂控制項視圖定義都必須定義至少一個型別名稱、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="dc78d-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="dc78d-122">如需自訂控制項視圖之元件的詳細資訊，請參閱[建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="dc78d-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dc78d-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc78d-123">See Also</span></span>

[<span data-ttu-id="dc78d-124">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="dc78d-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="dc78d-125">CustomEntry for View 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="dc78d-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="dc78d-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="dc78d-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
