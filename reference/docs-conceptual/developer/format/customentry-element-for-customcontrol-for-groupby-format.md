---
title: 適用于 CustomControl 之 GroupBy (格式的 CustomEntry 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4df8e5b96868b3814c6d84fa329950bb5345ef6e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785909"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="e4160-102">GroupBy 之 CustomControl 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e4160-102">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="e4160-103">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="e4160-103">Provides a definition of the control.</span></span> <span data-ttu-id="e4160-104">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="e4160-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e4160-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素（groupby (格式）) CustomEntries 元素（適用于 groupby (格式的 CustomEntry) CustomControl 元素） (</span><span class="sxs-lookup"><span data-stu-id="e4160-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e4160-106">語法</span><span class="sxs-lookup"><span data-stu-id="e4160-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e4160-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e4160-107">Attributes and Elements</span></span>

<span data-ttu-id="e4160-108">下列各節說明屬性、子專案和元素的父元素 `CustomEntry` 。</span><span class="sxs-lookup"><span data-stu-id="e4160-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e4160-109">屬性</span><span class="sxs-lookup"><span data-stu-id="e4160-109">Attributes</span></span>

<span data-ttu-id="e4160-110">無。</span><span class="sxs-lookup"><span data-stu-id="e4160-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e4160-111">子元素</span><span class="sxs-lookup"><span data-stu-id="e4160-111">Child Elements</span></span>

|<span data-ttu-id="e4160-112">元素</span><span class="sxs-lookup"><span data-stu-id="e4160-112">Element</span></span>|<span data-ttu-id="e4160-113">描述</span><span class="sxs-lookup"><span data-stu-id="e4160-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e4160-114">GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e4160-114">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="e4160-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="e4160-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e4160-116">定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="e4160-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="e4160-117">GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e4160-117">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="e4160-118">必要元素。</span><span class="sxs-lookup"><span data-stu-id="e4160-118">Required element.</span></span><br /><br /> <span data-ttu-id="e4160-119">定義控制項顯示資料的方式。</span><span class="sxs-lookup"><span data-stu-id="e4160-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e4160-120">父項目</span><span class="sxs-lookup"><span data-stu-id="e4160-120">Parent Elements</span></span>

|<span data-ttu-id="e4160-121">元素</span><span class="sxs-lookup"><span data-stu-id="e4160-121">Element</span></span>|<span data-ttu-id="e4160-122">描述</span><span class="sxs-lookup"><span data-stu-id="e4160-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e4160-123">GroupBy 之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e4160-123">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="e4160-124">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="e4160-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e4160-125">備註</span><span class="sxs-lookup"><span data-stu-id="e4160-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="e4160-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4160-126">See Also</span></span>

[<span data-ttu-id="e4160-127">GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e4160-127">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="e4160-128">GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e4160-128">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="e4160-129">GroupBy 之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e4160-129">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="e4160-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="e4160-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
