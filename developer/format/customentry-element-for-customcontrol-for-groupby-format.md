---
title: GroupBy （格式） 的 CustomControl CustomEntry 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860364"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="dc9cd-102">GroupBy 之 CustomControl 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dc9cd-102">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="dc9cd-103">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="dc9cd-103">Provides a definition of the control.</span></span> <span data-ttu-id="dc9cd-104">定義新的群組物件的顯示方式時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="dc9cd-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="dc9cd-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素GroupBy （格式） 的 CustomControl</span><span class="sxs-lookup"><span data-stu-id="dc9cd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dc9cd-106">語法</span><span class="sxs-lookup"><span data-stu-id="dc9cd-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dc9cd-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="dc9cd-107">Attributes and Elements</span></span>

<span data-ttu-id="dc9cd-108">下列各節說明屬性、 子項目，以及的父項目`CustomEntry`項目。</span><span class="sxs-lookup"><span data-stu-id="dc9cd-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dc9cd-109">屬性</span><span class="sxs-lookup"><span data-stu-id="dc9cd-109">Attributes</span></span>

<span data-ttu-id="dc9cd-110">無。</span><span class="sxs-lookup"><span data-stu-id="dc9cd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dc9cd-111">子元素</span><span class="sxs-lookup"><span data-stu-id="dc9cd-111">Child Elements</span></span>

|<span data-ttu-id="dc9cd-112">元素</span><span class="sxs-lookup"><span data-stu-id="dc9cd-112">Element</span></span>|<span data-ttu-id="dc9cd-113">描述</span><span class="sxs-lookup"><span data-stu-id="dc9cd-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dc9cd-114">GroupBy （格式） 的 CustomEntry EntrySelectedBy 項目</span><span class="sxs-lookup"><span data-stu-id="dc9cd-114">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="dc9cd-115">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="dc9cd-115">Optional element.</span></span><br /><br /> <span data-ttu-id="dc9cd-116">定義使用此控制項定義或必須存在於要使用此定義條件的.NET 類型。</span><span class="sxs-lookup"><span data-stu-id="dc9cd-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="dc9cd-117">GroupBy （格式） 的 CustomEntry CustomItem 項目</span><span class="sxs-lookup"><span data-stu-id="dc9cd-117">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="dc9cd-118">必要項目。</span><span class="sxs-lookup"><span data-stu-id="dc9cd-118">Required element.</span></span><br /><br /> <span data-ttu-id="dc9cd-119">定義控制項顯示資料的方式。</span><span class="sxs-lookup"><span data-stu-id="dc9cd-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dc9cd-120">父元素</span><span class="sxs-lookup"><span data-stu-id="dc9cd-120">Parent Elements</span></span>

|<span data-ttu-id="dc9cd-121">元素</span><span class="sxs-lookup"><span data-stu-id="dc9cd-121">Element</span></span>|<span data-ttu-id="dc9cd-122">描述</span><span class="sxs-lookup"><span data-stu-id="dc9cd-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dc9cd-123">GroupBy （格式） 的 CustomControl CustomEntries 項目</span><span class="sxs-lookup"><span data-stu-id="dc9cd-123">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="dc9cd-124">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="dc9cd-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dc9cd-125">備註</span><span class="sxs-lookup"><span data-stu-id="dc9cd-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="dc9cd-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc9cd-126">See Also</span></span>

[<span data-ttu-id="dc9cd-127">GroupBy （格式） 的 CustomEntry EntrySelectedBy 項目</span><span class="sxs-lookup"><span data-stu-id="dc9cd-127">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="dc9cd-128">GroupBy （格式） 的 CustomEntry CustomItem 項目</span><span class="sxs-lookup"><span data-stu-id="dc9cd-128">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="dc9cd-129">GroupBy （格式） 的 CustomControl CustomEntries 項目</span><span class="sxs-lookup"><span data-stu-id="dc9cd-129">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="dc9cd-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="dc9cd-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
