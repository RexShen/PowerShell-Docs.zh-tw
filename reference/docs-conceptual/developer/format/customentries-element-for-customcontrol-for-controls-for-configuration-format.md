---
title: CustomControl 之控制項的 CustomEntries 元素，用於設定 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b1f494cf1a254d71362830ba9eb0f4905a2a484d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785977"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="c04c9-102">設定之控制項的 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c04c9-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="c04c9-103">提供通用控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="c04c9-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="c04c9-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="c04c9-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="c04c9-105">Configuration 元素 (格式) Controls 設定的控制項元素 (格式設定的控制項) 控制項專案 (格式) 設定 (格式的 CustomControl CustomEntries 元素) </span><span class="sxs-lookup"><span data-stu-id="c04c9-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c04c9-106">語法</span><span class="sxs-lookup"><span data-stu-id="c04c9-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c04c9-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c04c9-107">Attributes and Elements</span></span>

<span data-ttu-id="c04c9-108">下列各節說明屬性、子專案和元素的父元素 `CustomEntries` 。</span><span class="sxs-lookup"><span data-stu-id="c04c9-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="c04c9-109">您必須指定一或多個子項目。</span><span class="sxs-lookup"><span data-stu-id="c04c9-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c04c9-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c04c9-110">Attributes</span></span>

<span data-ttu-id="c04c9-111">無。</span><span class="sxs-lookup"><span data-stu-id="c04c9-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c04c9-112">子元素</span><span class="sxs-lookup"><span data-stu-id="c04c9-112">Child Elements</span></span>

|<span data-ttu-id="c04c9-113">元素</span><span class="sxs-lookup"><span data-stu-id="c04c9-113">Element</span></span>|<span data-ttu-id="c04c9-114">描述</span><span class="sxs-lookup"><span data-stu-id="c04c9-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c04c9-115">設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c04c9-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="c04c9-116">提供通用控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="c04c9-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c04c9-117">父項目</span><span class="sxs-lookup"><span data-stu-id="c04c9-117">Parent Elements</span></span>

|<span data-ttu-id="c04c9-118">元素</span><span class="sxs-lookup"><span data-stu-id="c04c9-118">Element</span></span>|<span data-ttu-id="c04c9-119">描述</span><span class="sxs-lookup"><span data-stu-id="c04c9-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c04c9-120">CustomControl 元素，用於控制設定 (格式) </span><span class="sxs-lookup"><span data-stu-id="c04c9-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="c04c9-121">定義通用控制項。</span><span class="sxs-lookup"><span data-stu-id="c04c9-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c04c9-122">備註</span><span class="sxs-lookup"><span data-stu-id="c04c9-122">Remarks</span></span>

<span data-ttu-id="c04c9-123">在大部分情況下，控制項只有一個定義，定義在單一 `CustomEntry` 元素中。</span><span class="sxs-lookup"><span data-stu-id="c04c9-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="c04c9-124">不過，如果您想要使用相同的控制項來顯示不同的 .NET 物件，則可能會有多個定義。</span><span class="sxs-lookup"><span data-stu-id="c04c9-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="c04c9-125">在這些情況下，您可以定義 `CustomEntry` 每個物件或一組物件的元素。</span><span class="sxs-lookup"><span data-stu-id="c04c9-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="c04c9-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c04c9-126">See Also</span></span>

[<span data-ttu-id="c04c9-127">CustomControl 元素，用於控制設定 (格式) </span><span class="sxs-lookup"><span data-stu-id="c04c9-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="c04c9-128">設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c04c9-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="c04c9-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="c04c9-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
