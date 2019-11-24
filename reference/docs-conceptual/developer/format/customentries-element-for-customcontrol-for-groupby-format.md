---
title: GroupBy 之 CustomControl 的 CustomEntries 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364087"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="1220d-102">GroupBy 之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1220d-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="1220d-103">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="1220d-103">Provides the definitions for the control.</span></span> <span data-ttu-id="1220d-104">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="1220d-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="1220d-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（format） CustomEntries 元素（適用于 GroupBy 的 CustomControl）的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1220d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1220d-106">語法</span><span class="sxs-lookup"><span data-stu-id="1220d-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1220d-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="1220d-107">Attributes and Elements</span></span>

<span data-ttu-id="1220d-108">下列各節說明屬性、子專案，以及 `CustomEntries` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="1220d-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="1220d-109">可以指定的子項目數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="1220d-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="1220d-110">屬性</span><span class="sxs-lookup"><span data-stu-id="1220d-110">Attributes</span></span>

<span data-ttu-id="1220d-111">無。</span><span class="sxs-lookup"><span data-stu-id="1220d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1220d-112">子元素</span><span class="sxs-lookup"><span data-stu-id="1220d-112">Child Elements</span></span>

|<span data-ttu-id="1220d-113">項目</span><span class="sxs-lookup"><span data-stu-id="1220d-113">Element</span></span>|<span data-ttu-id="1220d-114">說明</span><span class="sxs-lookup"><span data-stu-id="1220d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1220d-115">GroupBy 之 CustomControl 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1220d-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="1220d-116">必要元素。</span><span class="sxs-lookup"><span data-stu-id="1220d-116">Required element.</span></span><br /><br /> <span data-ttu-id="1220d-117">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="1220d-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1220d-118">父元素</span><span class="sxs-lookup"><span data-stu-id="1220d-118">Parent Elements</span></span>

|<span data-ttu-id="1220d-119">項目</span><span class="sxs-lookup"><span data-stu-id="1220d-119">Element</span></span>|<span data-ttu-id="1220d-120">說明</span><span class="sxs-lookup"><span data-stu-id="1220d-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1220d-121">GroupBy 的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1220d-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="1220d-122">定義顯示新群組的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="1220d-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1220d-123">備註</span><span class="sxs-lookup"><span data-stu-id="1220d-123">Remarks</span></span>

<span data-ttu-id="1220d-124">在大部分情況下，控制項只有一個定義，在單一 `CustomEntry` 元素中指定。</span><span class="sxs-lookup"><span data-stu-id="1220d-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="1220d-125">不過，如果您想要使用相同的控制項來顯示不同的群組，也可以提供多個定義。</span><span class="sxs-lookup"><span data-stu-id="1220d-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="1220d-126">在這些情況下，您可以定義群組的 `CustomEntry` 元素。</span><span class="sxs-lookup"><span data-stu-id="1220d-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="1220d-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1220d-127">See Also</span></span>

[<span data-ttu-id="1220d-128">View 之控制項的 CustomEntries 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1220d-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="1220d-129">GroupBy 的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1220d-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="1220d-130">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="1220d-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
