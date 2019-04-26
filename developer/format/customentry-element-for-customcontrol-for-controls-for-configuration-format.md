---
title: CustomEntry CustomControl 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066460"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="0d9eb-102">設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0d9eb-102">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="0d9eb-103">提供通用控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="0d9eb-103">Provides a definition of the common control.</span></span> <span data-ttu-id="0d9eb-104">定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="0d9eb-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="0d9eb-105">組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目CustomControl 控制項組態 （格式） 的格式） CustomEntry 項目</span><span class="sxs-lookup"><span data-stu-id="0d9eb-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0d9eb-106">語法</span><span class="sxs-lookup"><span data-stu-id="0d9eb-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="0d9eb-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0d9eb-107">Attributes and Elements</span></span>

<span data-ttu-id="0d9eb-108">下列各節說明屬性、 子項目和父項目`CustomEntry`項目。</span><span class="sxs-lookup"><span data-stu-id="0d9eb-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="0d9eb-109">您必須指定定義所顯示的項目。</span><span class="sxs-lookup"><span data-stu-id="0d9eb-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="0d9eb-110">屬性</span><span class="sxs-lookup"><span data-stu-id="0d9eb-110">Attributes</span></span>

<span data-ttu-id="0d9eb-111">無。</span><span class="sxs-lookup"><span data-stu-id="0d9eb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0d9eb-112">子元素</span><span class="sxs-lookup"><span data-stu-id="0d9eb-112">Child Elements</span></span>

|<span data-ttu-id="0d9eb-113">元素</span><span class="sxs-lookup"><span data-stu-id="0d9eb-113">Element</span></span>|<span data-ttu-id="0d9eb-114">描述</span><span class="sxs-lookup"><span data-stu-id="0d9eb-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0d9eb-115">EntrySelectedBy CustomEntry 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="0d9eb-115">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="0d9eb-116">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="0d9eb-116">Optional element.</span></span><br /><br /> <span data-ttu-id="0d9eb-117">定義使用的通用控制項或條件必須存在於要使用這個控制項定義的.NET 類型。</span><span class="sxs-lookup"><span data-stu-id="0d9eb-117">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="0d9eb-118">組態控制項 CustomEntry CustomItem 項目</span><span class="sxs-lookup"><span data-stu-id="0d9eb-118">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="0d9eb-119">必要項目。</span><span class="sxs-lookup"><span data-stu-id="0d9eb-119">Required element.</span></span><br /><br /> <span data-ttu-id="0d9eb-120">定義控制項所顯示的資料和顯示方式。</span><span class="sxs-lookup"><span data-stu-id="0d9eb-120">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0d9eb-121">父項目</span><span class="sxs-lookup"><span data-stu-id="0d9eb-121">Parent Elements</span></span>

|<span data-ttu-id="0d9eb-122">項目</span><span class="sxs-lookup"><span data-stu-id="0d9eb-122">Element</span></span>|<span data-ttu-id="0d9eb-123">描述</span><span class="sxs-lookup"><span data-stu-id="0d9eb-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0d9eb-124">CustomEntries CustomControl 組態 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="0d9eb-124">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="0d9eb-125">提供通用控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="0d9eb-125">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0d9eb-126">備註</span><span class="sxs-lookup"><span data-stu-id="0d9eb-126">Remarks</span></span>

<span data-ttu-id="0d9eb-127">在大部分情況下，只有一個定義需要針對每個常見的自訂控制項，但可以有多個定義，如果您想要使用相同的控制項來顯示不同的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="0d9eb-127">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="0d9eb-128">在這些情況下，您可以針對每個物件或一組物件提供不同的定義。</span><span class="sxs-lookup"><span data-stu-id="0d9eb-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d9eb-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d9eb-129">See Also</span></span>

[<span data-ttu-id="0d9eb-130">CustomEntries CustomControl 組態 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="0d9eb-130">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="0d9eb-131">組態控制項 CustomEntry CustomItem 項目</span><span class="sxs-lookup"><span data-stu-id="0d9eb-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="0d9eb-132">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="0d9eb-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
