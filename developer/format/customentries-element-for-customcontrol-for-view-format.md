---
title: CustomEntries CustomControl 檢視 （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066510"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="50042-102">檢視之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="50042-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="50042-103">提供自訂的控制項檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="50042-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="50042-104">自訂控制項的檢視必須指定一個或多個定義。</span><span class="sxs-lookup"><span data-stu-id="50042-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="50042-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目 （格式） CustomEntries 項目 CustomControl 檢視 （格式）</span><span class="sxs-lookup"><span data-stu-id="50042-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="50042-106">語法</span><span class="sxs-lookup"><span data-stu-id="50042-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="50042-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="50042-107">Attributes and Elements</span></span>

<span data-ttu-id="50042-108">下列各節說明屬性、 子項目和父項目`CustomControlEntries`項目。</span><span class="sxs-lookup"><span data-stu-id="50042-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="50042-109">您必須指定一個以上的子項目。</span><span class="sxs-lookup"><span data-stu-id="50042-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="50042-110">屬性</span><span class="sxs-lookup"><span data-stu-id="50042-110">Attributes</span></span>

<span data-ttu-id="50042-111">無。</span><span class="sxs-lookup"><span data-stu-id="50042-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="50042-112">子元素</span><span class="sxs-lookup"><span data-stu-id="50042-112">Child Elements</span></span>

|<span data-ttu-id="50042-113">元素</span><span class="sxs-lookup"><span data-stu-id="50042-113">Element</span></span>|<span data-ttu-id="50042-114">描述</span><span class="sxs-lookup"><span data-stu-id="50042-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="50042-115">CustomEntry CustomEntries 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="50042-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="50042-116">必要項目。</span><span class="sxs-lookup"><span data-stu-id="50042-116">Required element.</span></span><br /><br /> <span data-ttu-id="50042-117">提供自訂的控制項檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="50042-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="50042-118">父項目</span><span class="sxs-lookup"><span data-stu-id="50042-118">Parent Elements</span></span>

|<span data-ttu-id="50042-119">項目</span><span class="sxs-lookup"><span data-stu-id="50042-119">Element</span></span>|<span data-ttu-id="50042-120">描述</span><span class="sxs-lookup"><span data-stu-id="50042-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="50042-121">CustomControl 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="50042-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="50042-122">必要項目。</span><span class="sxs-lookup"><span data-stu-id="50042-122">Required element.</span></span><br /><br /> <span data-ttu-id="50042-123">定義檢視的自訂控制項格式。</span><span class="sxs-lookup"><span data-stu-id="50042-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="50042-124">備註</span><span class="sxs-lookup"><span data-stu-id="50042-124">Remarks</span></span>

<span data-ttu-id="50042-125">在大部分情況下，控制項有只有一個定義，其定義於單一`CustomEntry`項目。</span><span class="sxs-lookup"><span data-stu-id="50042-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="50042-126">不過，它是可以有多個定義，如果您想要使用相同的控制項來顯示不同的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="50042-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="50042-127">在這些情況下，您可以定義`CustomEntry`每個物件或一組物件的項目。</span><span class="sxs-lookup"><span data-stu-id="50042-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="50042-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50042-128">See Also</span></span>

[<span data-ttu-id="50042-129">CustomControl 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="50042-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="50042-130">CustomEntry CustomEntries 檢視 （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="50042-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="50042-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="50042-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
