---
title: CustomEntries CustomControl 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066595"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="2c6d8-102">設定之控制項的 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2c6d8-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="2c6d8-103">提供通用控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="2c6d8-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="2c6d8-104">定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="2c6d8-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="2c6d8-105">組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目格式）</span><span class="sxs-lookup"><span data-stu-id="2c6d8-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2c6d8-106">語法</span><span class="sxs-lookup"><span data-stu-id="2c6d8-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="2c6d8-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2c6d8-107">Attributes and Elements</span></span>

<span data-ttu-id="2c6d8-108">下列各節說明屬性、 子項目和父項目`CustomEntries`項目。</span><span class="sxs-lookup"><span data-stu-id="2c6d8-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="2c6d8-109">您必須指定一個以上的子項目。</span><span class="sxs-lookup"><span data-stu-id="2c6d8-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2c6d8-110">屬性</span><span class="sxs-lookup"><span data-stu-id="2c6d8-110">Attributes</span></span>

<span data-ttu-id="2c6d8-111">無。</span><span class="sxs-lookup"><span data-stu-id="2c6d8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2c6d8-112">子元素</span><span class="sxs-lookup"><span data-stu-id="2c6d8-112">Child Elements</span></span>

|<span data-ttu-id="2c6d8-113">元素</span><span class="sxs-lookup"><span data-stu-id="2c6d8-113">Element</span></span>|<span data-ttu-id="2c6d8-114">描述</span><span class="sxs-lookup"><span data-stu-id="2c6d8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2c6d8-115">CustomEntry CustomControl 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="2c6d8-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="2c6d8-116">提供通用控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="2c6d8-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2c6d8-117">父項目</span><span class="sxs-lookup"><span data-stu-id="2c6d8-117">Parent Elements</span></span>

|<span data-ttu-id="2c6d8-118">項目</span><span class="sxs-lookup"><span data-stu-id="2c6d8-118">Element</span></span>|<span data-ttu-id="2c6d8-119">描述</span><span class="sxs-lookup"><span data-stu-id="2c6d8-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2c6d8-120">CustomControl 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="2c6d8-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="2c6d8-121">定義通用的控制項。</span><span class="sxs-lookup"><span data-stu-id="2c6d8-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2c6d8-122">備註</span><span class="sxs-lookup"><span data-stu-id="2c6d8-122">Remarks</span></span>

<span data-ttu-id="2c6d8-123">在大部分情況下，控制項有只有一個定義，其定義於單一`CustomEntry`項目。</span><span class="sxs-lookup"><span data-stu-id="2c6d8-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="2c6d8-124">不過，它是可以有多個定義，如果您想要使用相同的控制項來顯示不同的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="2c6d8-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="2c6d8-125">在這些情況下，您可以定義`CustomEntry`每個物件或一組物件的項目。</span><span class="sxs-lookup"><span data-stu-id="2c6d8-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="2c6d8-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c6d8-126">See Also</span></span>

[<span data-ttu-id="2c6d8-127">CustomControl 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="2c6d8-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="2c6d8-128">CustomEntry CustomControl 組態 （格式） 的控制項的項目</span><span class="sxs-lookup"><span data-stu-id="2c6d8-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="2c6d8-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="2c6d8-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
