---
title: 用於檢視 （格式） 的控制項 CustomControl CustomEntries 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861804"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="f328a-102">檢視之控制項的 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="f328a-102">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="f328a-103">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="f328a-103">Provides the definitions for the control.</span></span> <span data-ttu-id="f328a-104">定義可供檢視的控制項時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="f328a-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="f328a-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目用於檢視 （格式） 的控制項 CustomControl</span><span class="sxs-lookup"><span data-stu-id="f328a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f328a-106">語法</span><span class="sxs-lookup"><span data-stu-id="f328a-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f328a-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="f328a-107">Attributes and Elements</span></span>

<span data-ttu-id="f328a-108">下列各節說明屬性、 子項目和父項目`CustomEntries`項目。</span><span class="sxs-lookup"><span data-stu-id="f328a-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="f328a-109">沒有任何最大的限制，您可以指定的子項目數目。</span><span class="sxs-lookup"><span data-stu-id="f328a-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="f328a-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f328a-110">Attributes</span></span>

<span data-ttu-id="f328a-111">無。</span><span class="sxs-lookup"><span data-stu-id="f328a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f328a-112">子元素</span><span class="sxs-lookup"><span data-stu-id="f328a-112">Child Elements</span></span>

|<span data-ttu-id="f328a-113">元素</span><span class="sxs-lookup"><span data-stu-id="f328a-113">Element</span></span>|<span data-ttu-id="f328a-114">描述</span><span class="sxs-lookup"><span data-stu-id="f328a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f328a-115">用於檢視 （格式） 的控制項 CustomEntries CustomEntry 項目</span><span class="sxs-lookup"><span data-stu-id="f328a-115">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="f328a-116">必要項目。</span><span class="sxs-lookup"><span data-stu-id="f328a-116">Required element.</span></span><br /><br /> <span data-ttu-id="f328a-117">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="f328a-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f328a-118">父元素</span><span class="sxs-lookup"><span data-stu-id="f328a-118">Parent Elements</span></span>

|<span data-ttu-id="f328a-119">元素</span><span class="sxs-lookup"><span data-stu-id="f328a-119">Element</span></span>|<span data-ttu-id="f328a-120">描述</span><span class="sxs-lookup"><span data-stu-id="f328a-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f328a-121">用於檢視 （格式） 的控制項的控制項 CustomControl 項目</span><span class="sxs-lookup"><span data-stu-id="f328a-121">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="f328a-122">定義檢視所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="f328a-122">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f328a-123">備註</span><span class="sxs-lookup"><span data-stu-id="f328a-123">Remarks</span></span>

<span data-ttu-id="f328a-124">在大部分情況下，控制項有只有一個定義中，指定在單一`CustomEntry`項目。</span><span class="sxs-lookup"><span data-stu-id="f328a-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="f328a-125">不過，就可以提供多個定義，如果您想要使用相同的控制項來顯示不同的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="f328a-125">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="f328a-126">在這些情況下，您可以定義`CustomEntry`每個物件或一組物件的項目。</span><span class="sxs-lookup"><span data-stu-id="f328a-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="f328a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f328a-127">See Also</span></span>

[<span data-ttu-id="f328a-128">用於檢視 （格式） 的控制項 CustomEntries CustomEntry 項目</span><span class="sxs-lookup"><span data-stu-id="f328a-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="f328a-129">用於檢視 （格式） 的控制項的控制項 CustomControl 項目</span><span class="sxs-lookup"><span data-stu-id="f328a-129">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="f328a-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="f328a-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
