---
title: GroupBy （格式） 供標籤項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862394"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="b6445-102">GroupBy 的標籤元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b6445-102">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="b6445-103">指定在發現新的群組時，會顯示的標籤。</span><span class="sxs-lookup"><span data-stu-id="b6445-103">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="b6445-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） 的 GroupBy （格式） 的標籤項目</span><span class="sxs-lookup"><span data-stu-id="b6445-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b6445-105">語法</span><span class="sxs-lookup"><span data-stu-id="b6445-105">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b6445-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="b6445-106">Attributes and Elements</span></span>

<span data-ttu-id="b6445-107">下列各節說明屬性、 子項目和父項目`Label`項目。</span><span class="sxs-lookup"><span data-stu-id="b6445-107">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b6445-108">屬性</span><span class="sxs-lookup"><span data-stu-id="b6445-108">Attributes</span></span>

<span data-ttu-id="b6445-109">無。</span><span class="sxs-lookup"><span data-stu-id="b6445-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b6445-110">子元素</span><span class="sxs-lookup"><span data-stu-id="b6445-110">Child Elements</span></span>

<span data-ttu-id="b6445-111">無。</span><span class="sxs-lookup"><span data-stu-id="b6445-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b6445-112">父元素</span><span class="sxs-lookup"><span data-stu-id="b6445-112">Parent Elements</span></span>

|<span data-ttu-id="b6445-113">元素</span><span class="sxs-lookup"><span data-stu-id="b6445-113">Element</span></span>|<span data-ttu-id="b6445-114">描述</span><span class="sxs-lookup"><span data-stu-id="b6445-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b6445-115">檢視 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="b6445-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="b6445-116">定義新的一整組物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="b6445-116">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b6445-117">文字值</span><span class="sxs-lookup"><span data-stu-id="b6445-117">Text Value</span></span>

<span data-ttu-id="b6445-118">指定 Windows PowerShell 會遇到新的屬性或指令碼的值時，即顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="b6445-118">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="b6445-119">備註</span><span class="sxs-lookup"><span data-stu-id="b6445-119">Remarks</span></span>

<span data-ttu-id="b6445-120">除了這個項目所指定的文字，Windows PowerShell 會顯示新的值開始群組，並新增一個空白行之前, 和之後的群組。</span><span class="sxs-lookup"><span data-stu-id="b6445-120">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="b6445-121">範例</span><span class="sxs-lookup"><span data-stu-id="b6445-121">Example</span></span>

<span data-ttu-id="b6445-122">下列範例示範新的群組的標籤。</span><span class="sxs-lookup"><span data-stu-id="b6445-122">The following example shows the label for a new group.</span></span> <span data-ttu-id="b6445-123">顯示的標籤會看起來像這樣： `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="b6445-123">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="b6445-124">如需完整的格式化檔案，其中包含這個元素的範例，請參閱 <<c0> [ 寬型檢視 (GroupBy)](./wide-view-groupby.md)。</span><span class="sxs-lookup"><span data-stu-id="b6445-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b6445-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6445-125">See Also</span></span>

[<span data-ttu-id="b6445-126">檢視 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="b6445-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="b6445-127">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="b6445-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
