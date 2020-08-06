---
title: CustomControl for View (格式) 的 CustomEntries 的 CustomEntry 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a13e83ec941bed80eaab02e40131054432fcce00
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785875"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="068d1-102">檢視之 CustomControl 的 CustomEntries 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="068d1-102">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="068d1-103">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="068d1-103">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="068d1-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) CustomControl 元素 (format) CustomEntries 元素 for CustomControl for view (format) CustomEntry 元素 for View (Format) </span><span class="sxs-lookup"><span data-stu-id="068d1-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="068d1-105">語法</span><span class="sxs-lookup"><span data-stu-id="068d1-105">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="068d1-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="068d1-106">Attributes and Elements</span></span>

<span data-ttu-id="068d1-107">下列各節說明屬性、子專案和元素的父元素 `CustomEntry` 。</span><span class="sxs-lookup"><span data-stu-id="068d1-107">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="068d1-108">您必須指定定義所顯示的專案。</span><span class="sxs-lookup"><span data-stu-id="068d1-108">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="068d1-109">屬性</span><span class="sxs-lookup"><span data-stu-id="068d1-109">Attributes</span></span>

<span data-ttu-id="068d1-110">無。</span><span class="sxs-lookup"><span data-stu-id="068d1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="068d1-111">子元素</span><span class="sxs-lookup"><span data-stu-id="068d1-111">Child Elements</span></span>

|<span data-ttu-id="068d1-112">元素</span><span class="sxs-lookup"><span data-stu-id="068d1-112">Element</span></span>|<span data-ttu-id="068d1-113">描述</span><span class="sxs-lookup"><span data-stu-id="068d1-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="068d1-114">CustomEntry for View (格式的之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="068d1-114">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="068d1-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="068d1-115">Optional element.</span></span><br /><br /> <span data-ttu-id="068d1-116">定義使用自訂控制項視圖定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="068d1-116">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="068d1-117">CustomEntry for View (格式的 CustomItem 元素) </span><span class="sxs-lookup"><span data-stu-id="068d1-117">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="068d1-118">定義自訂控制項定義的控制項。</span><span class="sxs-lookup"><span data-stu-id="068d1-118">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="068d1-119">父項目</span><span class="sxs-lookup"><span data-stu-id="068d1-119">Parent Elements</span></span>

|<span data-ttu-id="068d1-120">元素</span><span class="sxs-lookup"><span data-stu-id="068d1-120">Element</span></span>|<span data-ttu-id="068d1-121">描述</span><span class="sxs-lookup"><span data-stu-id="068d1-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="068d1-122">檢視之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="068d1-122">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="068d1-123">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="068d1-123">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="068d1-124">自訂控制項視圖必須指定一或多個定義。</span><span class="sxs-lookup"><span data-stu-id="068d1-124">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="068d1-125">備註</span><span class="sxs-lookup"><span data-stu-id="068d1-125">Remarks</span></span>

<span data-ttu-id="068d1-126">在大部分的情況下，每個自訂控制項視圖都只需要一個定義，但是如果您想要使用相同的視圖來顯示不同的 .NET 物件，則可能會有多個定義。</span><span class="sxs-lookup"><span data-stu-id="068d1-126">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="068d1-127">在這些情況下，您可以為每個物件或一組物件提供個別的定義。</span><span class="sxs-lookup"><span data-stu-id="068d1-127">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="068d1-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="068d1-128">See Also</span></span>

[<span data-ttu-id="068d1-129">檢視的 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="068d1-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="068d1-130">CustomEntry for View (格式的 CustomItem 元素) </span><span class="sxs-lookup"><span data-stu-id="068d1-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="068d1-131">CustomEntry for View (格式的之 entryselectedby 元素) </span><span class="sxs-lookup"><span data-stu-id="068d1-131">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="068d1-132">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="068d1-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
