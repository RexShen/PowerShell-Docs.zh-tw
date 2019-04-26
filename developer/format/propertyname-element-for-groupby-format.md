---
title: GroupBy （格式） 的屬性名稱項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075863"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="12841-102">GroupBy 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="12841-102">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="12841-103">指定.NET 屬性，其值變更時，會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="12841-103">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="12841-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） 的 GroupBy （格式） 的屬性名稱項目</span><span class="sxs-lookup"><span data-stu-id="12841-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="12841-105">語法</span><span class="sxs-lookup"><span data-stu-id="12841-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="12841-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="12841-106">Attributes and Elements</span></span>

<span data-ttu-id="12841-107">下列各節說明屬性、 子項目和父項目`PropertyName`項目。</span><span class="sxs-lookup"><span data-stu-id="12841-107">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="12841-108">屬性</span><span class="sxs-lookup"><span data-stu-id="12841-108">Attributes</span></span>

<span data-ttu-id="12841-109">無。</span><span class="sxs-lookup"><span data-stu-id="12841-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="12841-110">子元素</span><span class="sxs-lookup"><span data-stu-id="12841-110">Child Elements</span></span>

<span data-ttu-id="12841-111">無。</span><span class="sxs-lookup"><span data-stu-id="12841-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="12841-112">父項目</span><span class="sxs-lookup"><span data-stu-id="12841-112">Parent Elements</span></span>

|<span data-ttu-id="12841-113">項目</span><span class="sxs-lookup"><span data-stu-id="12841-113">Element</span></span>|<span data-ttu-id="12841-114">描述</span><span class="sxs-lookup"><span data-stu-id="12841-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="12841-115">檢視 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="12841-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="12841-116">定義一組.NET 物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="12841-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="12841-117">文字值</span><span class="sxs-lookup"><span data-stu-id="12841-117">Text Value</span></span>

<span data-ttu-id="12841-118">指定.NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="12841-118">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="12841-119">備註</span><span class="sxs-lookup"><span data-stu-id="12841-119">Remarks</span></span>

<span data-ttu-id="12841-120">當這個屬性的值變更時，Windows PowerShell 會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="12841-120">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="12841-121">當指定這個項目時，您無法指定[ScriptBlock](./scriptblock-element-for-groupby-format.md)啟動新的群組項目。</span><span class="sxs-lookup"><span data-stu-id="12841-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="12841-122">範例</span><span class="sxs-lookup"><span data-stu-id="12841-122">Example</span></span>

<span data-ttu-id="12841-123">下列範例示範如何啟動新的群組屬性的值變更時。</span><span class="sxs-lookup"><span data-stu-id="12841-123">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="12841-124">如需完整的格式化檔案，其中包含這個元素的範例，請參閱 <<c0> [ 寬型檢視 (GroupBy)](./wide-view-groupby.md)。</span><span class="sxs-lookup"><span data-stu-id="12841-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="12841-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12841-125">See Also</span></span>

[<span data-ttu-id="12841-126">檢視 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="12841-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="12841-127">GroupBy （格式） 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="12841-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="12841-128">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="12841-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
