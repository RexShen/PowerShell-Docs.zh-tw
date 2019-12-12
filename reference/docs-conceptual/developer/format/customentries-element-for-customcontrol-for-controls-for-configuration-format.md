---
title: 設定之控制項的 CustomControl 的 CustomEntries 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368817"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="04550-102">設定之控制項的 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="04550-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="04550-103">提供通用控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="04550-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="04550-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="04550-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="04550-105">Configuration 元素（格式）控制設定（format） CustomControl 元素的設定（格式）控制項專案的設定專案（格式） CustomControl 設定的 CustomEntries 元素（格式）編排</span><span class="sxs-lookup"><span data-stu-id="04550-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="04550-106">語法</span><span class="sxs-lookup"><span data-stu-id="04550-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="04550-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="04550-107">Attributes and Elements</span></span>

<span data-ttu-id="04550-108">下列各節說明屬性、子專案，以及 `CustomEntries` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="04550-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="04550-109">您必須指定一或多個子項目。</span><span class="sxs-lookup"><span data-stu-id="04550-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="04550-110">屬性</span><span class="sxs-lookup"><span data-stu-id="04550-110">Attributes</span></span>

<span data-ttu-id="04550-111">無。</span><span class="sxs-lookup"><span data-stu-id="04550-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="04550-112">子元素</span><span class="sxs-lookup"><span data-stu-id="04550-112">Child Elements</span></span>

|<span data-ttu-id="04550-113">元素</span><span class="sxs-lookup"><span data-stu-id="04550-113">Element</span></span>|<span data-ttu-id="04550-114">描述</span><span class="sxs-lookup"><span data-stu-id="04550-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="04550-115">設定之控制項的 CustomControl 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="04550-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="04550-116">提供通用控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="04550-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="04550-117">父元素</span><span class="sxs-lookup"><span data-stu-id="04550-117">Parent Elements</span></span>

|<span data-ttu-id="04550-118">元素</span><span class="sxs-lookup"><span data-stu-id="04550-118">Element</span></span>|<span data-ttu-id="04550-119">描述</span><span class="sxs-lookup"><span data-stu-id="04550-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="04550-120">設定之控制項的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="04550-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="04550-121">定義通用控制項。</span><span class="sxs-lookup"><span data-stu-id="04550-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="04550-122">備註</span><span class="sxs-lookup"><span data-stu-id="04550-122">Remarks</span></span>

<span data-ttu-id="04550-123">在大部分的情況下，控制項只有一個定義，在單一 `CustomEntry` 專案中定義。</span><span class="sxs-lookup"><span data-stu-id="04550-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="04550-124">不過，如果您想要使用相同的控制項來顯示不同的 .NET 物件，則可能會有多個定義。</span><span class="sxs-lookup"><span data-stu-id="04550-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="04550-125">在這些情況下，您可以為每個物件或一組物件定義一個 `CustomEntry` 元素。</span><span class="sxs-lookup"><span data-stu-id="04550-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="04550-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04550-126">See Also</span></span>

[<span data-ttu-id="04550-127">設定之控制項的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="04550-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="04550-128">設定之控制項的 CustomControl 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="04550-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="04550-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="04550-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
