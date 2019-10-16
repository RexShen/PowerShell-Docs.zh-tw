---
title: CustomControl for View 的 CustomEntries 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364077"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="692b5-102">檢視之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="692b5-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="692b5-103">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="692b5-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="692b5-104">自訂控制項視圖必須指定一或多個定義。</span><span class="sxs-lookup"><span data-stu-id="692b5-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="692b5-105">CustomControl for View 的設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素（格式） CustomEntries 元素</span><span class="sxs-lookup"><span data-stu-id="692b5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="692b5-106">語法</span><span class="sxs-lookup"><span data-stu-id="692b5-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="692b5-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="692b5-107">Attributes and Elements</span></span>

<span data-ttu-id="692b5-108">下列各節說明屬性、子專案，以及 `CustomControlEntries` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="692b5-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="692b5-109">您必須指定一或多個子項目。</span><span class="sxs-lookup"><span data-stu-id="692b5-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="692b5-110">屬性</span><span class="sxs-lookup"><span data-stu-id="692b5-110">Attributes</span></span>

<span data-ttu-id="692b5-111">無。</span><span class="sxs-lookup"><span data-stu-id="692b5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="692b5-112">子元素</span><span class="sxs-lookup"><span data-stu-id="692b5-112">Child Elements</span></span>

|<span data-ttu-id="692b5-113">元素</span><span class="sxs-lookup"><span data-stu-id="692b5-113">Element</span></span>|<span data-ttu-id="692b5-114">描述</span><span class="sxs-lookup"><span data-stu-id="692b5-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="692b5-115">CustomEntries for View 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="692b5-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="692b5-116">必要元素。</span><span class="sxs-lookup"><span data-stu-id="692b5-116">Required element.</span></span><br /><br /> <span data-ttu-id="692b5-117">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="692b5-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="692b5-118">父元素</span><span class="sxs-lookup"><span data-stu-id="692b5-118">Parent Elements</span></span>

|<span data-ttu-id="692b5-119">元素</span><span class="sxs-lookup"><span data-stu-id="692b5-119">Element</span></span>|<span data-ttu-id="692b5-120">描述</span><span class="sxs-lookup"><span data-stu-id="692b5-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="692b5-121">View 的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="692b5-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="692b5-122">必要元素。</span><span class="sxs-lookup"><span data-stu-id="692b5-122">Required element.</span></span><br /><br /> <span data-ttu-id="692b5-123">定義視圖的自訂控制項格式。</span><span class="sxs-lookup"><span data-stu-id="692b5-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="692b5-124">備註</span><span class="sxs-lookup"><span data-stu-id="692b5-124">Remarks</span></span>

<span data-ttu-id="692b5-125">在大部分的情況下，控制項只有一個定義，定義在單一 @no__t 0 元素中。</span><span class="sxs-lookup"><span data-stu-id="692b5-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="692b5-126">不過，如果您想要使用相同的控制項來顯示不同的 .NET 物件，則可能會有多個定義。</span><span class="sxs-lookup"><span data-stu-id="692b5-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="692b5-127">在這些情況下，您可以為每個物件或一組物件定義一個 @no__t 0 元素。</span><span class="sxs-lookup"><span data-stu-id="692b5-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="692b5-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="692b5-128">See Also</span></span>

[<span data-ttu-id="692b5-129">View 的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="692b5-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="692b5-130">CustomEntries for View 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="692b5-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="692b5-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="692b5-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
