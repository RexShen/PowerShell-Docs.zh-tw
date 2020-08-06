---
title: View (Format) 的控制項之 CustomControl 的 CustomEntries 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a52bd2368044c34a0b73da331785d55597e30260
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783699"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="b8d84-102">檢視之控制項的 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b8d84-102">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="b8d84-103">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="b8d84-103">Provides the definitions for the control.</span></span> <span data-ttu-id="b8d84-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="b8d84-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b8d84-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 CustomControl 格式 (CustomEntries 元素用於視圖) 格式的控制項 (的專案</span><span class="sxs-lookup"><span data-stu-id="b8d84-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b8d84-106">語法</span><span class="sxs-lookup"><span data-stu-id="b8d84-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b8d84-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b8d84-107">Attributes and Elements</span></span>

<span data-ttu-id="b8d84-108">下列各節描述元素的屬性、子專案和父項目 `CustomEntries` 。</span><span class="sxs-lookup"><span data-stu-id="b8d84-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="b8d84-109">可以指定的子項目數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="b8d84-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="b8d84-110">屬性</span><span class="sxs-lookup"><span data-stu-id="b8d84-110">Attributes</span></span>

<span data-ttu-id="b8d84-111">無。</span><span class="sxs-lookup"><span data-stu-id="b8d84-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b8d84-112">子元素</span><span class="sxs-lookup"><span data-stu-id="b8d84-112">Child Elements</span></span>

|<span data-ttu-id="b8d84-113">元素</span><span class="sxs-lookup"><span data-stu-id="b8d84-113">Element</span></span>|<span data-ttu-id="b8d84-114">描述</span><span class="sxs-lookup"><span data-stu-id="b8d84-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b8d84-115">檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b8d84-115">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="b8d84-116">必要元素。</span><span class="sxs-lookup"><span data-stu-id="b8d84-116">Required element.</span></span><br /><br /> <span data-ttu-id="b8d84-117">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="b8d84-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b8d84-118">父項目</span><span class="sxs-lookup"><span data-stu-id="b8d84-118">Parent Elements</span></span>

|<span data-ttu-id="b8d84-119">元素</span><span class="sxs-lookup"><span data-stu-id="b8d84-119">Element</span></span>|<span data-ttu-id="b8d84-120">描述</span><span class="sxs-lookup"><span data-stu-id="b8d84-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b8d84-121">檢視之控制項的控制項 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b8d84-121">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="b8d84-122">定義視圖所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="b8d84-122">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b8d84-123">備註</span><span class="sxs-lookup"><span data-stu-id="b8d84-123">Remarks</span></span>

<span data-ttu-id="b8d84-124">在大部分情況下，控制項只有一個定義，在單一元素中指定 `CustomEntry` 。</span><span class="sxs-lookup"><span data-stu-id="b8d84-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="b8d84-125">不過，如果您想要使用相同的控制項來顯示不同的 .NET 物件，就可以提供多個定義。</span><span class="sxs-lookup"><span data-stu-id="b8d84-125">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="b8d84-126">在這些情況下，您可以定義 `CustomEntry` 每個物件或一組物件的元素。</span><span class="sxs-lookup"><span data-stu-id="b8d84-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8d84-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8d84-127">See Also</span></span>

[<span data-ttu-id="b8d84-128">檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b8d84-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="b8d84-129">檢視之控制項的控制項 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b8d84-129">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="b8d84-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="b8d84-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
