---
title: GroupBy （格式） 的 EntrySelectedBy TypeName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861664"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="8ad9b-102">GroupBy 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8ad9b-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="8ad9b-103">指定會使用這個定義的自訂控制項的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="8ad9b-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="8ad9b-104">定義新的群組物件的顯示方式時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="8ad9b-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="8ad9b-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素CustomControl CustomEntry EntrySelectedBy 的 GroupBy （格式） 的 GroupBy （格式） 類型名稱元素的 GroupBy （格式） EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="8ad9b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8ad9b-106">語法</span><span class="sxs-lookup"><span data-stu-id="8ad9b-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8ad9b-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="8ad9b-107">Attributes and Elements</span></span>

<span data-ttu-id="8ad9b-108">下列各節說明屬性、 子項目和父項目`TypeName`項目。</span><span class="sxs-lookup"><span data-stu-id="8ad9b-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8ad9b-109">屬性</span><span class="sxs-lookup"><span data-stu-id="8ad9b-109">Attributes</span></span>

<span data-ttu-id="8ad9b-110">無。</span><span class="sxs-lookup"><span data-stu-id="8ad9b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8ad9b-111">子元素</span><span class="sxs-lookup"><span data-stu-id="8ad9b-111">Child Elements</span></span>

<span data-ttu-id="8ad9b-112">無。</span><span class="sxs-lookup"><span data-stu-id="8ad9b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8ad9b-113">父元素</span><span class="sxs-lookup"><span data-stu-id="8ad9b-113">Parent Elements</span></span>

|<span data-ttu-id="8ad9b-114">元素</span><span class="sxs-lookup"><span data-stu-id="8ad9b-114">Element</span></span>|<span data-ttu-id="8ad9b-115">描述</span><span class="sxs-lookup"><span data-stu-id="8ad9b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8ad9b-116">GroupBy （格式） 的 CustomEntry EntrySelectedBy 項目</span><span class="sxs-lookup"><span data-stu-id="8ad9b-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="8ad9b-117">定義使用此控制項定義或必須存在於要使用此定義條件的.NET 類型。</span><span class="sxs-lookup"><span data-stu-id="8ad9b-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8ad9b-118">文字值</span><span class="sxs-lookup"><span data-stu-id="8ad9b-118">Text Value</span></span>

<span data-ttu-id="8ad9b-119">指定完整的.NET 型別名稱，例如`System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="8ad9b-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="8ad9b-120">備註</span><span class="sxs-lookup"><span data-stu-id="8ad9b-120">Remarks</span></span>

<span data-ttu-id="8ad9b-121">每個控制項定義必須至少一個型別名稱、 選取項目集或選擇條件的定義。</span><span class="sxs-lookup"><span data-stu-id="8ad9b-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="8ad9b-122">如需詳細的自訂控制項的檢視元件的相關資訊，請參閱[建立自訂控制項](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="8ad9b-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8ad9b-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ad9b-123">See Also</span></span>

[<span data-ttu-id="8ad9b-124">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="8ad9b-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="8ad9b-125">GroupBy （格式） 的 CustomEntry EntrySelectedBy 項目</span><span class="sxs-lookup"><span data-stu-id="8ad9b-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="8ad9b-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="8ad9b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
