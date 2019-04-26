---
title: TypeName SelectionCondition 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 477c8711-fffc-4f92-af45-6d4f80990474
caps.latest.revision: 7
ms.openlocfilehash: 60f02f3240c5574e1b1f9027b060bd9af89a11d2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083938"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="5acd6-102">設定之控制項的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5acd6-102">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="5acd6-103">指定觸發條件的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="5acd6-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="5acd6-104">定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="5acd6-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="5acd6-105">組態 （格式） 的組態 （格式） CustomControl 項目控制項的 CustomControl 的組態 （格式） CustomEntries 項目控制項的控制項的控制項項目的組態項目 （格式） 的控制項項目針對 CustomEntry 的 EntrySelectedBy 的組態 （格式） SelectionCondition 項目控制項的 CustomEntry 的組態 （格式） EntrySelectedBy 項目控制項的 CustomControl 的組態 （格式） CustomEntry 項目SelectionCondition 控制項組態 （格式） 的組態 （格式） 類型名稱項目</span><span class="sxs-lookup"><span data-stu-id="5acd6-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5acd6-106">語法</span><span class="sxs-lookup"><span data-stu-id="5acd6-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="5acd6-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5acd6-107">Attributes and Elements</span></span>

<span data-ttu-id="5acd6-108">下列各節說明屬性、 子項目和父項目`TypeName`項目。</span><span class="sxs-lookup"><span data-stu-id="5acd6-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5acd6-109">屬性</span><span class="sxs-lookup"><span data-stu-id="5acd6-109">Attributes</span></span>

<span data-ttu-id="5acd6-110">無。</span><span class="sxs-lookup"><span data-stu-id="5acd6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5acd6-111">子元素</span><span class="sxs-lookup"><span data-stu-id="5acd6-111">Child Elements</span></span>

<span data-ttu-id="5acd6-112">無。</span><span class="sxs-lookup"><span data-stu-id="5acd6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5acd6-113">父項目</span><span class="sxs-lookup"><span data-stu-id="5acd6-113">Parent Elements</span></span>

|<span data-ttu-id="5acd6-114">項目</span><span class="sxs-lookup"><span data-stu-id="5acd6-114">Element</span></span>|<span data-ttu-id="5acd6-115">描述</span><span class="sxs-lookup"><span data-stu-id="5acd6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5acd6-116">CustomEntry 組態 （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="5acd6-116">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="5acd6-117">定義必須存在，要使用的控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="5acd6-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5acd6-118">文字值</span><span class="sxs-lookup"><span data-stu-id="5acd6-118">Text Value</span></span>

<span data-ttu-id="5acd6-119">指定完整的.NET 型別名稱，例如`System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="5acd6-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="5acd6-120">備註</span><span class="sxs-lookup"><span data-stu-id="5acd6-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="5acd6-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5acd6-121">See Also</span></span>

[<span data-ttu-id="5acd6-122">CustomEntry 組態 （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="5acd6-122">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="5acd6-123">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="5acd6-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
