---
title: CustomControl for View (格式) 的 CustomEntries 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c89eb25f6922a92e2c18298d0128c4c2ca93df3d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785960"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="d56fa-102">檢視之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d56fa-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="d56fa-103">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="d56fa-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="d56fa-104">自訂控制項視圖必須指定一或多個定義。</span><span class="sxs-lookup"><span data-stu-id="d56fa-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="d56fa-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) CustomControl 元素 (format) CustomEntries 元素 for View (Format) </span><span class="sxs-lookup"><span data-stu-id="d56fa-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d56fa-106">語法</span><span class="sxs-lookup"><span data-stu-id="d56fa-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d56fa-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d56fa-107">Attributes and Elements</span></span>

<span data-ttu-id="d56fa-108">下列各節說明屬性、子專案和元素的父元素 `CustomControlEntries` 。</span><span class="sxs-lookup"><span data-stu-id="d56fa-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="d56fa-109">您必須指定一或多個子項目。</span><span class="sxs-lookup"><span data-stu-id="d56fa-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d56fa-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d56fa-110">Attributes</span></span>

<span data-ttu-id="d56fa-111">無。</span><span class="sxs-lookup"><span data-stu-id="d56fa-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d56fa-112">子元素</span><span class="sxs-lookup"><span data-stu-id="d56fa-112">Child Elements</span></span>

|<span data-ttu-id="d56fa-113">元素</span><span class="sxs-lookup"><span data-stu-id="d56fa-113">Element</span></span>|<span data-ttu-id="d56fa-114">描述</span><span class="sxs-lookup"><span data-stu-id="d56fa-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d56fa-115">CustomEntries for View (格式的 CustomEntry 元素) </span><span class="sxs-lookup"><span data-stu-id="d56fa-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="d56fa-116">必要元素。</span><span class="sxs-lookup"><span data-stu-id="d56fa-116">Required element.</span></span><br /><br /> <span data-ttu-id="d56fa-117">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="d56fa-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d56fa-118">父項目</span><span class="sxs-lookup"><span data-stu-id="d56fa-118">Parent Elements</span></span>

|<span data-ttu-id="d56fa-119">元素</span><span class="sxs-lookup"><span data-stu-id="d56fa-119">Element</span></span>|<span data-ttu-id="d56fa-120">描述</span><span class="sxs-lookup"><span data-stu-id="d56fa-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d56fa-121">檢視的 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d56fa-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="d56fa-122">必要元素。</span><span class="sxs-lookup"><span data-stu-id="d56fa-122">Required element.</span></span><br /><br /> <span data-ttu-id="d56fa-123">定義視圖的自訂控制項格式。</span><span class="sxs-lookup"><span data-stu-id="d56fa-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d56fa-124">備註</span><span class="sxs-lookup"><span data-stu-id="d56fa-124">Remarks</span></span>

<span data-ttu-id="d56fa-125">在大部分情況下，控制項只有一個定義，定義在單一 `CustomEntry` 元素中。</span><span class="sxs-lookup"><span data-stu-id="d56fa-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="d56fa-126">不過，如果您想要使用相同的控制項來顯示不同的 .NET 物件，則可能會有多個定義。</span><span class="sxs-lookup"><span data-stu-id="d56fa-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="d56fa-127">在這些情況下，您可以定義 `CustomEntry` 每個物件或一組物件的元素。</span><span class="sxs-lookup"><span data-stu-id="d56fa-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="d56fa-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d56fa-128">See Also</span></span>

[<span data-ttu-id="d56fa-129">檢視的 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d56fa-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="d56fa-130">CustomEntries for View (格式的 CustomEntry 元素) </span><span class="sxs-lookup"><span data-stu-id="d56fa-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d56fa-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="d56fa-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
