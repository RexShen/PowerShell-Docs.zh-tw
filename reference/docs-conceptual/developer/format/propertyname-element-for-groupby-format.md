---
title: GroupBy 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362517"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="84bb9-102">GroupBy 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="84bb9-102">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="84bb9-103">指定在每次其值變更時啟動新群組的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="84bb9-103">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="84bb9-104">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（格式） GroupBy （格式）的 PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="84bb9-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="84bb9-105">語法</span><span class="sxs-lookup"><span data-stu-id="84bb9-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="84bb9-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="84bb9-106">Attributes and Elements</span></span>

<span data-ttu-id="84bb9-107">下列各節說明屬性、子專案，以及 `PropertyName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="84bb9-107">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="84bb9-108">屬性</span><span class="sxs-lookup"><span data-stu-id="84bb9-108">Attributes</span></span>

<span data-ttu-id="84bb9-109">無。</span><span class="sxs-lookup"><span data-stu-id="84bb9-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="84bb9-110">子元素</span><span class="sxs-lookup"><span data-stu-id="84bb9-110">Child Elements</span></span>

<span data-ttu-id="84bb9-111">無。</span><span class="sxs-lookup"><span data-stu-id="84bb9-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="84bb9-112">父元素</span><span class="sxs-lookup"><span data-stu-id="84bb9-112">Parent Elements</span></span>

|<span data-ttu-id="84bb9-113">元素</span><span class="sxs-lookup"><span data-stu-id="84bb9-113">Element</span></span>|<span data-ttu-id="84bb9-114">描述</span><span class="sxs-lookup"><span data-stu-id="84bb9-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="84bb9-115">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="84bb9-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="84bb9-116">定義一組 .NET 物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="84bb9-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="84bb9-117">文字值</span><span class="sxs-lookup"><span data-stu-id="84bb9-117">Text Value</span></span>

<span data-ttu-id="84bb9-118">指定 .NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="84bb9-118">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="84bb9-119">備註</span><span class="sxs-lookup"><span data-stu-id="84bb9-119">Remarks</span></span>

<span data-ttu-id="84bb9-120">每當這個屬性的值變更時，Windows PowerShell 就會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="84bb9-120">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="84bb9-121">當指定此元素時，您無法指定[ScriptBlock](./scriptblock-element-for-groupby-format.md)元素來啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="84bb9-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="84bb9-122">範例</span><span class="sxs-lookup"><span data-stu-id="84bb9-122">Example</span></span>

<span data-ttu-id="84bb9-123">下列範例示範當屬性的值變更時，如何啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="84bb9-123">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="84bb9-124">如需包含此元素之完整格式檔案的範例，請參閱[寬視圖（GroupBy）](./wide-view-groupby.md)。</span><span class="sxs-lookup"><span data-stu-id="84bb9-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="84bb9-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84bb9-125">See Also</span></span>

[<span data-ttu-id="84bb9-126">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="84bb9-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="84bb9-127">GroupBy 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="84bb9-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="84bb9-128">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="84bb9-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
