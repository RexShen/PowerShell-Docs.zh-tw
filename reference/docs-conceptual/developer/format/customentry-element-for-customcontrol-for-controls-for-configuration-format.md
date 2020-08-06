---
title: CustomControl 之控制項的 CustomEntry 元素，用於設定 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8b9d18bbb1abce8135f4c27418ad54a1736eb5a6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785926"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="22e4c-102">設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="22e4c-102">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="22e4c-103">提供通用控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="22e4c-103">Provides a definition of the common control.</span></span> <span data-ttu-id="22e4c-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="22e4c-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="22e4c-105">Configuration 專案 (格式) Controls 設定的控制項元素 (格式設定的控制項) 控制項專案 (格式) 設定 (格式的 CustomControl 的 CustomEntries 元素) 格式 (CustomEntry 元素適用于 configuration) 格式的控制項 (</span><span class="sxs-lookup"><span data-stu-id="22e4c-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="22e4c-106">語法</span><span class="sxs-lookup"><span data-stu-id="22e4c-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="22e4c-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="22e4c-107">Attributes and Elements</span></span>

<span data-ttu-id="22e4c-108">下列各節說明屬性、子專案和元素的父元素 `CustomEntry` 。</span><span class="sxs-lookup"><span data-stu-id="22e4c-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="22e4c-109">您必須指定定義所顯示的專案。</span><span class="sxs-lookup"><span data-stu-id="22e4c-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="22e4c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="22e4c-110">Attributes</span></span>

<span data-ttu-id="22e4c-111">無。</span><span class="sxs-lookup"><span data-stu-id="22e4c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="22e4c-112">子元素</span><span class="sxs-lookup"><span data-stu-id="22e4c-112">Child Elements</span></span>

|<span data-ttu-id="22e4c-113">元素</span><span class="sxs-lookup"><span data-stu-id="22e4c-113">Element</span></span>|<span data-ttu-id="22e4c-114">描述</span><span class="sxs-lookup"><span data-stu-id="22e4c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="22e4c-115">設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="22e4c-115">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="22e4c-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="22e4c-116">Optional element.</span></span><br /><br /> <span data-ttu-id="22e4c-117">定義使用通用控制項定義的 .NET 類型，或必須存在才能使用此控制項的條件。</span><span class="sxs-lookup"><span data-stu-id="22e4c-117">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="22e4c-118">設定之控制項的 CustomEntry 的 CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="22e4c-118">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="22e4c-119">必要元素。</span><span class="sxs-lookup"><span data-stu-id="22e4c-119">Required element.</span></span><br /><br /> <span data-ttu-id="22e4c-120">定義控制項所顯示的資料及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="22e4c-120">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="22e4c-121">父項目</span><span class="sxs-lookup"><span data-stu-id="22e4c-121">Parent Elements</span></span>

|<span data-ttu-id="22e4c-122">元素</span><span class="sxs-lookup"><span data-stu-id="22e4c-122">Element</span></span>|<span data-ttu-id="22e4c-123">描述</span><span class="sxs-lookup"><span data-stu-id="22e4c-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="22e4c-124">CustomControl 的 CustomEntries 元素，用於設定 (格式) </span><span class="sxs-lookup"><span data-stu-id="22e4c-124">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="22e4c-125">提供通用控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="22e4c-125">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="22e4c-126">備註</span><span class="sxs-lookup"><span data-stu-id="22e4c-126">Remarks</span></span>

<span data-ttu-id="22e4c-127">在大部分情況下，每個一般自訂控制項只需要一個定義，但是如果您想要使用相同的控制項來顯示不同的 .NET 物件，則可以有多個定義。</span><span class="sxs-lookup"><span data-stu-id="22e4c-127">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="22e4c-128">在這些情況下，您可以為每個物件或一組物件提供個別的定義。</span><span class="sxs-lookup"><span data-stu-id="22e4c-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="22e4c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22e4c-129">See Also</span></span>

[<span data-ttu-id="22e4c-130">CustomControl 的 CustomEntries 元素，用於設定 (格式) </span><span class="sxs-lookup"><span data-stu-id="22e4c-130">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="22e4c-131">設定之控制項的 CustomEntry 的 CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="22e4c-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="22e4c-132">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="22e4c-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
