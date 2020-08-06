---
title: GroupBy (格式的 PropertyName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e83ebd49e4f3087c817b3cc8772889dbe85113aa
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785603"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="8b308-102">GroupBy 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8b308-102">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="8b308-103">指定在每次其值變更時啟動新群組的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="8b308-103">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="8b308-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素用於 GroupBy (格式) </span><span class="sxs-lookup"><span data-stu-id="8b308-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8b308-105">語法</span><span class="sxs-lookup"><span data-stu-id="8b308-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8b308-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8b308-106">Attributes and Elements</span></span>

<span data-ttu-id="8b308-107">下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="8b308-107">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8b308-108">屬性</span><span class="sxs-lookup"><span data-stu-id="8b308-108">Attributes</span></span>

<span data-ttu-id="8b308-109">無。</span><span class="sxs-lookup"><span data-stu-id="8b308-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8b308-110">子元素</span><span class="sxs-lookup"><span data-stu-id="8b308-110">Child Elements</span></span>

<span data-ttu-id="8b308-111">無。</span><span class="sxs-lookup"><span data-stu-id="8b308-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8b308-112">父項目</span><span class="sxs-lookup"><span data-stu-id="8b308-112">Parent Elements</span></span>

|<span data-ttu-id="8b308-113">元素</span><span class="sxs-lookup"><span data-stu-id="8b308-113">Element</span></span>|<span data-ttu-id="8b308-114">描述</span><span class="sxs-lookup"><span data-stu-id="8b308-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8b308-115">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8b308-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="8b308-116">定義一組 .NET 物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="8b308-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8b308-117">文字值</span><span class="sxs-lookup"><span data-stu-id="8b308-117">Text Value</span></span>

<span data-ttu-id="8b308-118">指定 .NET 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="8b308-118">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="8b308-119">備註</span><span class="sxs-lookup"><span data-stu-id="8b308-119">Remarks</span></span>

<span data-ttu-id="8b308-120">每當這個屬性的值變更時，Windows PowerShell 就會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="8b308-120">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="8b308-121">當指定此元素時，您無法指定[ScriptBlock](./scriptblock-element-for-groupby-format.md)元素來啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="8b308-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="8b308-122">範例</span><span class="sxs-lookup"><span data-stu-id="8b308-122">Example</span></span>

<span data-ttu-id="8b308-123">下列範例示範當屬性的值變更時，如何啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="8b308-123">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="8b308-124">如需包含此元素的完整格式檔案範例，請參閱[Wide View (GroupBy) ](./wide-view-groupby.md)。</span><span class="sxs-lookup"><span data-stu-id="8b308-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8b308-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b308-125">See Also</span></span>

[<span data-ttu-id="8b308-126">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8b308-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="8b308-127">GroupBy 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8b308-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="8b308-128">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="8b308-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
