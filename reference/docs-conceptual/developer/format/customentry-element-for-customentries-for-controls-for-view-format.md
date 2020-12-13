---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)
description: 檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)
ms.openlocfilehash: a525b198c8f595e04dc0804d36b5533b94f43c6b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646086"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="2caa4-103">檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2caa4-103">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="2caa4-104">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="2caa4-104">Provides a definition of the control.</span></span> <span data-ttu-id="2caa4-105">當定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="2caa4-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="2caa4-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 專案 (格式) 控制項專案 (格式) 控制項專案 (格式) CustomEntries 專案 (格式) 專案 (格式)  (格式控制項的控制項) 格式元素格式 CustomEntry 專案的控制項格式</span><span class="sxs-lookup"><span data-stu-id="2caa4-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2caa4-107">語法</span><span class="sxs-lookup"><span data-stu-id="2caa4-107">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2caa4-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2caa4-108">Attributes and Elements</span></span>

<span data-ttu-id="2caa4-109">下列各節說明屬性、子專案和元素的父元素 `CustomEntry` 。</span><span class="sxs-lookup"><span data-stu-id="2caa4-109">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2caa4-110">屬性</span><span class="sxs-lookup"><span data-stu-id="2caa4-110">Attributes</span></span>

<span data-ttu-id="2caa4-111">無。</span><span class="sxs-lookup"><span data-stu-id="2caa4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2caa4-112">子元素</span><span class="sxs-lookup"><span data-stu-id="2caa4-112">Child Elements</span></span>

|<span data-ttu-id="2caa4-113">元素</span><span class="sxs-lookup"><span data-stu-id="2caa4-113">Element</span></span>|<span data-ttu-id="2caa4-114">描述</span><span class="sxs-lookup"><span data-stu-id="2caa4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2caa4-115">檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2caa4-115">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="2caa4-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="2caa4-116">Optional element.</span></span><br /><br /> <span data-ttu-id="2caa4-117">定義使用此控制項定義的 .NET 型別，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="2caa4-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="2caa4-118">檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2caa4-118">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="2caa4-119">必要元素。</span><span class="sxs-lookup"><span data-stu-id="2caa4-119">Required element.</span></span><br /><br /> <span data-ttu-id="2caa4-120">定義控制項顯示資料的方式。</span><span class="sxs-lookup"><span data-stu-id="2caa4-120">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2caa4-121">父項目</span><span class="sxs-lookup"><span data-stu-id="2caa4-121">Parent Elements</span></span>

|<span data-ttu-id="2caa4-122">元素</span><span class="sxs-lookup"><span data-stu-id="2caa4-122">Element</span></span>|<span data-ttu-id="2caa4-123">描述</span><span class="sxs-lookup"><span data-stu-id="2caa4-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2caa4-124">檢視之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2caa4-124">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="2caa4-125">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="2caa4-125">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2caa4-126">備註</span><span class="sxs-lookup"><span data-stu-id="2caa4-126">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="2caa4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2caa4-127">See Also</span></span>

[<span data-ttu-id="2caa4-128">檢視之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2caa4-128">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2caa4-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="2caa4-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
