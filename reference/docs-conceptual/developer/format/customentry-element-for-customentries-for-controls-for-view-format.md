---
title: View 之控制項的 CustomEntries 的 CustomEntry 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364047"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="ae8f8-102">檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ae8f8-102">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="ae8f8-103">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="ae8f8-103">Provides a definition of the control.</span></span> <span data-ttu-id="ae8f8-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="ae8f8-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="ae8f8-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素CustomControl for View （Format） CustomEntry 元素，用於 CustomEntries 的 View （Format）控制項</span><span class="sxs-lookup"><span data-stu-id="ae8f8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ae8f8-106">語法</span><span class="sxs-lookup"><span data-stu-id="ae8f8-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ae8f8-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="ae8f8-107">Attributes and Elements</span></span>

<span data-ttu-id="ae8f8-108">下列各節說明屬性、子專案，以及 `CustomEntry` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="ae8f8-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ae8f8-109">屬性</span><span class="sxs-lookup"><span data-stu-id="ae8f8-109">Attributes</span></span>

<span data-ttu-id="ae8f8-110">無。</span><span class="sxs-lookup"><span data-stu-id="ae8f8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ae8f8-111">子元素</span><span class="sxs-lookup"><span data-stu-id="ae8f8-111">Child Elements</span></span>

|<span data-ttu-id="ae8f8-112">元素</span><span class="sxs-lookup"><span data-stu-id="ae8f8-112">Element</span></span>|<span data-ttu-id="ae8f8-113">描述</span><span class="sxs-lookup"><span data-stu-id="ae8f8-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ae8f8-114">View 之控制項的 CustomEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ae8f8-114">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="ae8f8-115">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="ae8f8-115">Optional element.</span></span><br /><br /> <span data-ttu-id="ae8f8-116">定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="ae8f8-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="ae8f8-117">View 之控制項的 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ae8f8-117">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="ae8f8-118">必要元素。</span><span class="sxs-lookup"><span data-stu-id="ae8f8-118">Required element.</span></span><br /><br /> <span data-ttu-id="ae8f8-119">定義控制項顯示資料的方式。</span><span class="sxs-lookup"><span data-stu-id="ae8f8-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ae8f8-120">父元素</span><span class="sxs-lookup"><span data-stu-id="ae8f8-120">Parent Elements</span></span>

|<span data-ttu-id="ae8f8-121">元素</span><span class="sxs-lookup"><span data-stu-id="ae8f8-121">Element</span></span>|<span data-ttu-id="ae8f8-122">描述</span><span class="sxs-lookup"><span data-stu-id="ae8f8-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ae8f8-123">CustomControl for View 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ae8f8-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="ae8f8-124">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="ae8f8-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ae8f8-125">備註</span><span class="sxs-lookup"><span data-stu-id="ae8f8-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="ae8f8-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae8f8-126">See Also</span></span>

[<span data-ttu-id="ae8f8-127">CustomControl for View 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ae8f8-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ae8f8-128">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="ae8f8-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
