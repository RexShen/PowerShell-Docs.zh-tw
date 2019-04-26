---
title: GroupBy （格式） 的 CustomControl CustomEntries 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066529"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="fee4c-102">GroupBy 之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fee4c-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="fee4c-103">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="fee4c-103">Provides the definitions for the control.</span></span> <span data-ttu-id="fee4c-104">定義新的群組物件的顯示方式時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="fee4c-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="fee4c-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 元素 CustomControl 的 GroupBy （格式） 的 GroupBy （格式） CustomEntries 元素的檢視 （格式） CustomControl 項目</span><span class="sxs-lookup"><span data-stu-id="fee4c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fee4c-106">語法</span><span class="sxs-lookup"><span data-stu-id="fee4c-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fee4c-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fee4c-107">Attributes and Elements</span></span>

<span data-ttu-id="fee4c-108">下列各節說明屬性、 子項目和父項目`CustomEntries`項目。</span><span class="sxs-lookup"><span data-stu-id="fee4c-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="fee4c-109">沒有任何最大的限制，您可以指定的子項目數目。</span><span class="sxs-lookup"><span data-stu-id="fee4c-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="fee4c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="fee4c-110">Attributes</span></span>

<span data-ttu-id="fee4c-111">無。</span><span class="sxs-lookup"><span data-stu-id="fee4c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fee4c-112">子元素</span><span class="sxs-lookup"><span data-stu-id="fee4c-112">Child Elements</span></span>

|<span data-ttu-id="fee4c-113">元素</span><span class="sxs-lookup"><span data-stu-id="fee4c-113">Element</span></span>|<span data-ttu-id="fee4c-114">描述</span><span class="sxs-lookup"><span data-stu-id="fee4c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fee4c-115">GroupBy （格式） 的 CustomControl CustomEntry 項目</span><span class="sxs-lookup"><span data-stu-id="fee4c-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="fee4c-116">必要項目。</span><span class="sxs-lookup"><span data-stu-id="fee4c-116">Required element.</span></span><br /><br /> <span data-ttu-id="fee4c-117">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="fee4c-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fee4c-118">父項目</span><span class="sxs-lookup"><span data-stu-id="fee4c-118">Parent Elements</span></span>

|<span data-ttu-id="fee4c-119">項目</span><span class="sxs-lookup"><span data-stu-id="fee4c-119">Element</span></span>|<span data-ttu-id="fee4c-120">描述</span><span class="sxs-lookup"><span data-stu-id="fee4c-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fee4c-121">CustomControl GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="fee4c-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="fee4c-122">定義自訂控制項，則會顯示新的群組。</span><span class="sxs-lookup"><span data-stu-id="fee4c-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fee4c-123">備註</span><span class="sxs-lookup"><span data-stu-id="fee4c-123">Remarks</span></span>

<span data-ttu-id="fee4c-124">在大部分情況下，控制項有只有一個定義中，指定在單一`CustomEntry`項目。</span><span class="sxs-lookup"><span data-stu-id="fee4c-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="fee4c-125">不過，就可以提供多個定義，如果您想要使用相同的控制項來顯示不同的群組。</span><span class="sxs-lookup"><span data-stu-id="fee4c-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="fee4c-126">在這些情況下，您可以定義`CustomEntry`群組的項目。</span><span class="sxs-lookup"><span data-stu-id="fee4c-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="fee4c-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fee4c-127">See Also</span></span>

[<span data-ttu-id="fee4c-128">用於檢視 （格式） 的控制項 CustomEntries CustomEntry 項目</span><span class="sxs-lookup"><span data-stu-id="fee4c-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="fee4c-129">CustomControl GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="fee4c-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="fee4c-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="fee4c-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
