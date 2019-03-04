---
title: CustomEntry 檢視 （格式） 的 EntrySelectedBy TypeName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858834"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="1915c-102">檢視之 CustomEntry 的 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1915c-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="1915c-103">指定使用自訂的控制項檢視此定義的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="1915c-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="1915c-104">類型可定義指定的數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="1915c-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="1915c-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目 （格式） CustomEntries 項目 CustomControl 檢視 （格式） 的檢視 （格式） EntrySelectedBy CustomEntries CustomEntry 元素CustomEntry 檢視 （格式） 類型名稱的項目為 EntrySelectedBy CustomEntry 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="1915c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1915c-106">語法</span><span class="sxs-lookup"><span data-stu-id="1915c-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1915c-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="1915c-107">Attributes and Elements</span></span>

<span data-ttu-id="1915c-108">下列各節說明屬性、 子項目和父項目`TypeName`項目。</span><span class="sxs-lookup"><span data-stu-id="1915c-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1915c-109">屬性</span><span class="sxs-lookup"><span data-stu-id="1915c-109">Attributes</span></span>

<span data-ttu-id="1915c-110">無。</span><span class="sxs-lookup"><span data-stu-id="1915c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1915c-111">子元素</span><span class="sxs-lookup"><span data-stu-id="1915c-111">Child Elements</span></span>

<span data-ttu-id="1915c-112">無。</span><span class="sxs-lookup"><span data-stu-id="1915c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1915c-113">父元素</span><span class="sxs-lookup"><span data-stu-id="1915c-113">Parent Elements</span></span>

|<span data-ttu-id="1915c-114">元素</span><span class="sxs-lookup"><span data-stu-id="1915c-114">Element</span></span>|<span data-ttu-id="1915c-115">描述</span><span class="sxs-lookup"><span data-stu-id="1915c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1915c-116">EntrySelectedBy CustomEntry 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="1915c-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="1915c-117">定義使用此自訂控制項的檢視定義的.NET 類型或必須存在於要使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="1915c-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1915c-118">文字值</span><span class="sxs-lookup"><span data-stu-id="1915c-118">Text Value</span></span>

<span data-ttu-id="1915c-119">指定完整的.NET 型別名稱，例如`System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="1915c-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="1915c-120">備註</span><span class="sxs-lookup"><span data-stu-id="1915c-120">Remarks</span></span>

<span data-ttu-id="1915c-121">每個自訂控制項的檢視定義必須至少一個型別名稱、 選取項目集或選擇條件的定義。</span><span class="sxs-lookup"><span data-stu-id="1915c-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="1915c-122">如需詳細的自訂控制項的檢視元件的相關資訊，請參閱[建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="1915c-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1915c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1915c-123">See Also</span></span>

[<span data-ttu-id="1915c-124">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="1915c-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="1915c-125">EntrySelectedBy CustomEntry 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="1915c-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1915c-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="1915c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
