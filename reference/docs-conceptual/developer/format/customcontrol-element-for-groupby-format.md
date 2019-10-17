---
title: GroupBy 的 CustomControl 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2472e256-8f4f-4288-8b67-a3300649dafa
caps.latest.revision: 9
ms.openlocfilehash: 2e84e770a345e272d4c5917b00afe7520840e1db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368957"
---
# <a name="customcontrol-element-for-groupby-format"></a><span data-ttu-id="962db-102">GroupBy 的 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="962db-102">CustomControl Element for GroupBy (Format)</span></span>

<span data-ttu-id="962db-103">定義顯示新群組的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="962db-103">Defines the custom control that displays the new group.</span></span>

<span data-ttu-id="962db-104">ViewDefinitions 元素（格式）的專案（格式） View 元素（格式） groupby 元素（格式） GroupBy 的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="962db-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="962db-105">語法</span><span class="sxs-lookup"><span data-stu-id="962db-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
<CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="962db-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="962db-106">Attributes and Elements</span></span>

<span data-ttu-id="962db-107">下列各節說明 `CustomControl` 元素的屬性、子專案和父元素。</span><span class="sxs-lookup"><span data-stu-id="962db-107">The following sections describe the attributes, child elements, and parent element of the `CustomControl` element.</span></span> <span data-ttu-id="962db-108">您可以指定任意數目的子項目，並依任何順序列出它們。</span><span class="sxs-lookup"><span data-stu-id="962db-108">You can specify any number of child elements and list them in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="962db-109">屬性</span><span class="sxs-lookup"><span data-stu-id="962db-109">Attributes</span></span>

<span data-ttu-id="962db-110">無。</span><span class="sxs-lookup"><span data-stu-id="962db-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="962db-111">子元素</span><span class="sxs-lookup"><span data-stu-id="962db-111">Child Elements</span></span>

|<span data-ttu-id="962db-112">元素</span><span class="sxs-lookup"><span data-stu-id="962db-112">Element</span></span>|<span data-ttu-id="962db-113">描述</span><span class="sxs-lookup"><span data-stu-id="962db-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="962db-114">GroupBy 之 CustomControl 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="962db-114">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="962db-115">必要元素。</span><span class="sxs-lookup"><span data-stu-id="962db-115">Required element.</span></span><br /><br /> <span data-ttu-id="962db-116">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="962db-116">Provides the definitions for the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="962db-117">父元素</span><span class="sxs-lookup"><span data-stu-id="962db-117">Parent Elements</span></span>

|<span data-ttu-id="962db-118">元素</span><span class="sxs-lookup"><span data-stu-id="962db-118">Element</span></span>|<span data-ttu-id="962db-119">描述</span><span class="sxs-lookup"><span data-stu-id="962db-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="962db-120">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="962db-120">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="962db-121">定義 Windows PowerShell 如何顯示新的物件群組。</span><span class="sxs-lookup"><span data-stu-id="962db-121">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="962db-122">備註</span><span class="sxs-lookup"><span data-stu-id="962db-122">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="962db-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="962db-123">See Also</span></span>

[<span data-ttu-id="962db-124">GroupBy 之 CustomControl 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="962db-124">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="962db-125">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="962db-125">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="962db-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="962db-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)