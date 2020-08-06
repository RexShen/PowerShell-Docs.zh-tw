---
title: 適用于 CustomControl 之 GroupBy (格式的 CustomEntries 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2221d1bb94159697ff10466e4606d6d54e117e30
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785943"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="c50b8-102">GroupBy 之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c50b8-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="c50b8-103">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="c50b8-103">Provides the definitions for the control.</span></span> <span data-ttu-id="c50b8-104">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="c50b8-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="c50b8-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素（GroupBy (格式）) CustomEntries 專案（適用于 GroupBy (格式的 CustomControl）) </span><span class="sxs-lookup"><span data-stu-id="c50b8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c50b8-106">語法</span><span class="sxs-lookup"><span data-stu-id="c50b8-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c50b8-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c50b8-107">Attributes and Elements</span></span>

<span data-ttu-id="c50b8-108">下列各節描述元素的屬性、子專案和父項目 `CustomEntries` 。</span><span class="sxs-lookup"><span data-stu-id="c50b8-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="c50b8-109">可以指定的子項目數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="c50b8-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="c50b8-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c50b8-110">Attributes</span></span>

<span data-ttu-id="c50b8-111">無。</span><span class="sxs-lookup"><span data-stu-id="c50b8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c50b8-112">子元素</span><span class="sxs-lookup"><span data-stu-id="c50b8-112">Child Elements</span></span>

|<span data-ttu-id="c50b8-113">元素</span><span class="sxs-lookup"><span data-stu-id="c50b8-113">Element</span></span>|<span data-ttu-id="c50b8-114">描述</span><span class="sxs-lookup"><span data-stu-id="c50b8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c50b8-115">GroupBy 之 CustomControl 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c50b8-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="c50b8-116">必要元素。</span><span class="sxs-lookup"><span data-stu-id="c50b8-116">Required element.</span></span><br /><br /> <span data-ttu-id="c50b8-117">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="c50b8-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c50b8-118">父項目</span><span class="sxs-lookup"><span data-stu-id="c50b8-118">Parent Elements</span></span>

|<span data-ttu-id="c50b8-119">元素</span><span class="sxs-lookup"><span data-stu-id="c50b8-119">Element</span></span>|<span data-ttu-id="c50b8-120">描述</span><span class="sxs-lookup"><span data-stu-id="c50b8-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c50b8-121">GroupBy 的 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c50b8-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="c50b8-122">定義顯示新群組的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="c50b8-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c50b8-123">備註</span><span class="sxs-lookup"><span data-stu-id="c50b8-123">Remarks</span></span>

<span data-ttu-id="c50b8-124">在大部分情況下，控制項只有一個定義，在單一元素中指定 `CustomEntry` 。</span><span class="sxs-lookup"><span data-stu-id="c50b8-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="c50b8-125">不過，如果您想要使用相同的控制項來顯示不同的群組，也可以提供多個定義。</span><span class="sxs-lookup"><span data-stu-id="c50b8-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="c50b8-126">在這些情況下，您可以定義 `CustomEntry` 群組的元素。</span><span class="sxs-lookup"><span data-stu-id="c50b8-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="c50b8-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c50b8-127">See Also</span></span>

[<span data-ttu-id="c50b8-128">檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c50b8-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="c50b8-129">GroupBy 的 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c50b8-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="c50b8-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="c50b8-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
