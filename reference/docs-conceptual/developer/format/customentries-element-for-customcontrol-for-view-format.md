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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364077"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="9fda8-102">檢視之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="9fda8-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="9fda8-103">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="9fda8-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="9fda8-104">自訂控制項視圖必須指定一或多個定義。</span><span class="sxs-lookup"><span data-stu-id="9fda8-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="9fda8-105">CustomControl for View 的設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素（格式） CustomEntries 元素</span><span class="sxs-lookup"><span data-stu-id="9fda8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9fda8-106">語法</span><span class="sxs-lookup"><span data-stu-id="9fda8-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9fda8-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="9fda8-107">Attributes and Elements</span></span>

<span data-ttu-id="9fda8-108">下列各節說明屬性、子專案，以及 `CustomControlEntries` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="9fda8-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="9fda8-109">您必須指定一或多個子項目。</span><span class="sxs-lookup"><span data-stu-id="9fda8-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9fda8-110">屬性</span><span class="sxs-lookup"><span data-stu-id="9fda8-110">Attributes</span></span>

<span data-ttu-id="9fda8-111">無。</span><span class="sxs-lookup"><span data-stu-id="9fda8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9fda8-112">子元素</span><span class="sxs-lookup"><span data-stu-id="9fda8-112">Child Elements</span></span>

|<span data-ttu-id="9fda8-113">元素</span><span class="sxs-lookup"><span data-stu-id="9fda8-113">Element</span></span>|<span data-ttu-id="9fda8-114">描述</span><span class="sxs-lookup"><span data-stu-id="9fda8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9fda8-115">CustomEntries for View 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9fda8-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="9fda8-116">必要項目。</span><span class="sxs-lookup"><span data-stu-id="9fda8-116">Required element.</span></span><br /><br /> <span data-ttu-id="9fda8-117">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="9fda8-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9fda8-118">父元素</span><span class="sxs-lookup"><span data-stu-id="9fda8-118">Parent Elements</span></span>

|<span data-ttu-id="9fda8-119">元素</span><span class="sxs-lookup"><span data-stu-id="9fda8-119">Element</span></span>|<span data-ttu-id="9fda8-120">描述</span><span class="sxs-lookup"><span data-stu-id="9fda8-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9fda8-121">View 的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9fda8-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="9fda8-122">必要項目。</span><span class="sxs-lookup"><span data-stu-id="9fda8-122">Required element.</span></span><br /><br /> <span data-ttu-id="9fda8-123">定義視圖的自訂控制項格式。</span><span class="sxs-lookup"><span data-stu-id="9fda8-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9fda8-124">備註</span><span class="sxs-lookup"><span data-stu-id="9fda8-124">Remarks</span></span>

<span data-ttu-id="9fda8-125">在大部分的情況下，控制項只有一個定義，在單一 `CustomEntry` 專案中定義。</span><span class="sxs-lookup"><span data-stu-id="9fda8-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="9fda8-126">不過，如果您想要使用相同的控制項來顯示不同的 .NET 物件，則可能會有多個定義。</span><span class="sxs-lookup"><span data-stu-id="9fda8-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="9fda8-127">在這些情況下，您可以為每個物件或一組物件定義一個 `CustomEntry` 元素。</span><span class="sxs-lookup"><span data-stu-id="9fda8-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="9fda8-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fda8-128">See Also</span></span>

[<span data-ttu-id="9fda8-129">View 的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9fda8-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="9fda8-130">CustomEntries for View 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9fda8-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9fda8-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="9fda8-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
