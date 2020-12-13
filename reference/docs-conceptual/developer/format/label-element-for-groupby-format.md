---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 的標籤元素 (格式)
description: GroupBy 的標籤元素 (格式)
ms.openlocfilehash: ff4b0dec01bb5b472b1813540661791b91568eed
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649798"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="2be99-103">GroupBy 的標籤元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2be99-103">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="2be99-104">指定當遇到新群組時所顯示的標籤。</span><span class="sxs-lookup"><span data-stu-id="2be99-104">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="2be99-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) groupby 的 GroupBy 專案 (格式) GroupBy (格式的 Label 元素) </span><span class="sxs-lookup"><span data-stu-id="2be99-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2be99-106">語法</span><span class="sxs-lookup"><span data-stu-id="2be99-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2be99-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2be99-107">Attributes and Elements</span></span>

<span data-ttu-id="2be99-108">下列各節描述專案的屬性、子項目和父元素 `Label` 。</span><span class="sxs-lookup"><span data-stu-id="2be99-108">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2be99-109">屬性</span><span class="sxs-lookup"><span data-stu-id="2be99-109">Attributes</span></span>

<span data-ttu-id="2be99-110">無。</span><span class="sxs-lookup"><span data-stu-id="2be99-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2be99-111">子元素</span><span class="sxs-lookup"><span data-stu-id="2be99-111">Child Elements</span></span>

<span data-ttu-id="2be99-112">無。</span><span class="sxs-lookup"><span data-stu-id="2be99-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2be99-113">父項目</span><span class="sxs-lookup"><span data-stu-id="2be99-113">Parent Elements</span></span>

|<span data-ttu-id="2be99-114">元素</span><span class="sxs-lookup"><span data-stu-id="2be99-114">Element</span></span>|<span data-ttu-id="2be99-115">描述</span><span class="sxs-lookup"><span data-stu-id="2be99-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2be99-116">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2be99-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="2be99-117">定義如何顯示新的物件群組。</span><span class="sxs-lookup"><span data-stu-id="2be99-117">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2be99-118">文字值</span><span class="sxs-lookup"><span data-stu-id="2be99-118">Text Value</span></span>

<span data-ttu-id="2be99-119">指定每當 Windows PowerShell 遇到新的屬性或腳本值時，所顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="2be99-119">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="2be99-120">備註</span><span class="sxs-lookup"><span data-stu-id="2be99-120">Remarks</span></span>

<span data-ttu-id="2be99-121">除了這個專案所指定的文字之外，Windows PowerShell 會顯示啟動群組的新值，並在群組前後加入空白行。</span><span class="sxs-lookup"><span data-stu-id="2be99-121">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="2be99-122">範例</span><span class="sxs-lookup"><span data-stu-id="2be99-122">Example</span></span>

<span data-ttu-id="2be99-123">下列範例顯示新群組的標籤。</span><span class="sxs-lookup"><span data-stu-id="2be99-123">The following example shows the label for a new group.</span></span> <span data-ttu-id="2be99-124">顯示的標籤看起來會像這樣： `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="2be99-124">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="2be99-125">如需包含此專案之完整格式化檔案的範例，請參閱 [Wide View (GroupBy) ](./wide-view-groupby.md)。</span><span class="sxs-lookup"><span data-stu-id="2be99-125">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2be99-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2be99-126">See Also</span></span>

[<span data-ttu-id="2be99-127">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2be99-127">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="2be99-128">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="2be99-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
