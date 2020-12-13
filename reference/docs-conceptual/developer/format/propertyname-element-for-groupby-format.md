---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 的 PropertyName 元素 (格式)
description: GroupBy 的 PropertyName 元素 (格式)
ms.openlocfilehash: 44351c46ff2386f967644fef4f423b3858dc1619
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666139"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="dd9c3-103">GroupBy 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dd9c3-103">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="dd9c3-104">指定每當新群組值變更時，會啟動新群組的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="dd9c3-104">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="dd9c3-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) groupby (格式的 groupby 元素) </span><span class="sxs-lookup"><span data-stu-id="dd9c3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dd9c3-106">語法</span><span class="sxs-lookup"><span data-stu-id="dd9c3-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dd9c3-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dd9c3-107">Attributes and Elements</span></span>

<span data-ttu-id="dd9c3-108">下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="dd9c3-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dd9c3-109">屬性</span><span class="sxs-lookup"><span data-stu-id="dd9c3-109">Attributes</span></span>

<span data-ttu-id="dd9c3-110">無。</span><span class="sxs-lookup"><span data-stu-id="dd9c3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dd9c3-111">子元素</span><span class="sxs-lookup"><span data-stu-id="dd9c3-111">Child Elements</span></span>

<span data-ttu-id="dd9c3-112">無。</span><span class="sxs-lookup"><span data-stu-id="dd9c3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dd9c3-113">父項目</span><span class="sxs-lookup"><span data-stu-id="dd9c3-113">Parent Elements</span></span>

|<span data-ttu-id="dd9c3-114">元素</span><span class="sxs-lookup"><span data-stu-id="dd9c3-114">Element</span></span>|<span data-ttu-id="dd9c3-115">描述</span><span class="sxs-lookup"><span data-stu-id="dd9c3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dd9c3-116">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dd9c3-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="dd9c3-117">定義如何顯示 .NET 物件的群組。</span><span class="sxs-lookup"><span data-stu-id="dd9c3-117">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dd9c3-118">文字值</span><span class="sxs-lookup"><span data-stu-id="dd9c3-118">Text Value</span></span>

<span data-ttu-id="dd9c3-119">指定 .NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="dd9c3-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="dd9c3-120">備註</span><span class="sxs-lookup"><span data-stu-id="dd9c3-120">Remarks</span></span>

<span data-ttu-id="dd9c3-121">每當這個屬性的值變更時，Windows PowerShell 就會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="dd9c3-121">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="dd9c3-122">當指定這個專案時，您無法指定 [ScriptBlock](./scriptblock-element-for-groupby-format.md) 元素來啟動新群組。</span><span class="sxs-lookup"><span data-stu-id="dd9c3-122">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="dd9c3-123">範例</span><span class="sxs-lookup"><span data-stu-id="dd9c3-123">Example</span></span>

<span data-ttu-id="dd9c3-124">下列範例示範如何在屬性值變更時，啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="dd9c3-124">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="dd9c3-125">如需包含此專案之完整格式化檔案的範例，請參閱 [Wide View (GroupBy) ](./wide-view-groupby.md)。</span><span class="sxs-lookup"><span data-stu-id="dd9c3-125">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dd9c3-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd9c3-126">See Also</span></span>

[<span data-ttu-id="dd9c3-127">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dd9c3-127">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="dd9c3-128">GroupBy 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dd9c3-128">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="dd9c3-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="dd9c3-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
