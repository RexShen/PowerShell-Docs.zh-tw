---
title: 設定之控制項的 CustomControl 的 CustomEntry 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364067"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="dcb92-102">設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dcb92-102">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="dcb92-103">提供通用控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="dcb92-103">Provides a definition of the common control.</span></span> <span data-ttu-id="dcb92-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="dcb92-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="dcb92-105">Configuration 元素（格式）控制設定（format） CustomControl 元素的設定（格式）控制項專案的設定專案（格式） CustomControl 設定的 CustomEntries 元素（格式）Format）用於設定之控制項 CustomControl 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="dcb92-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dcb92-106">語法</span><span class="sxs-lookup"><span data-stu-id="dcb92-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="dcb92-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="dcb92-107">Attributes and Elements</span></span>

<span data-ttu-id="dcb92-108">下列各節說明屬性、子專案，以及 `CustomEntry` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="dcb92-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="dcb92-109">您必須指定定義所顯示的專案。</span><span class="sxs-lookup"><span data-stu-id="dcb92-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="dcb92-110">屬性</span><span class="sxs-lookup"><span data-stu-id="dcb92-110">Attributes</span></span>

<span data-ttu-id="dcb92-111">無。</span><span class="sxs-lookup"><span data-stu-id="dcb92-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dcb92-112">子元素</span><span class="sxs-lookup"><span data-stu-id="dcb92-112">Child Elements</span></span>

|<span data-ttu-id="dcb92-113">元素</span><span class="sxs-lookup"><span data-stu-id="dcb92-113">Element</span></span>|<span data-ttu-id="dcb92-114">描述</span><span class="sxs-lookup"><span data-stu-id="dcb92-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dcb92-115">設定之控制項的 CustomEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="dcb92-115">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="dcb92-116">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="dcb92-116">Optional element.</span></span><br /><br /> <span data-ttu-id="dcb92-117">定義使用通用控制項定義的 .NET 類型，或必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="dcb92-117">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="dcb92-118">設定之控制項的 CustomEntry 的 CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="dcb92-118">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="dcb92-119">必要元素。</span><span class="sxs-lookup"><span data-stu-id="dcb92-119">Required element.</span></span><br /><br /> <span data-ttu-id="dcb92-120">定義控制項所顯示的資料及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="dcb92-120">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dcb92-121">父元素</span><span class="sxs-lookup"><span data-stu-id="dcb92-121">Parent Elements</span></span>

|<span data-ttu-id="dcb92-122">元素</span><span class="sxs-lookup"><span data-stu-id="dcb92-122">Element</span></span>|<span data-ttu-id="dcb92-123">描述</span><span class="sxs-lookup"><span data-stu-id="dcb92-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dcb92-124">設定之 CustomControl 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="dcb92-124">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="dcb92-125">提供通用控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="dcb92-125">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dcb92-126">備註</span><span class="sxs-lookup"><span data-stu-id="dcb92-126">Remarks</span></span>

<span data-ttu-id="dcb92-127">在大部分情況下，每個一般自訂控制項只需要一個定義，但是如果您想要使用相同的控制項來顯示不同的 .NET 物件，則可以有多個定義。</span><span class="sxs-lookup"><span data-stu-id="dcb92-127">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="dcb92-128">在這些情況下，您可以為每個物件或一組物件提供個別的定義。</span><span class="sxs-lookup"><span data-stu-id="dcb92-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="dcb92-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcb92-129">See Also</span></span>

[<span data-ttu-id="dcb92-130">設定之 CustomControl 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="dcb92-130">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="dcb92-131">設定之控制項的 CustomEntry 的 CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="dcb92-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="dcb92-132">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="dcb92-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
