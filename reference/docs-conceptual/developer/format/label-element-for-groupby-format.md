---
title: GroupBy (格式的標籤元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 07b4d037472a9dd2329e94576ec10f5b82f46b34
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785773"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="68927-102">GroupBy 的標籤元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="68927-102">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="68927-103">指定遇到新群組時所顯示的標籤。</span><span class="sxs-lookup"><span data-stu-id="68927-103">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="68927-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素，用於 GroupBy (格式) 標籤元素 (</span><span class="sxs-lookup"><span data-stu-id="68927-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="68927-105">語法</span><span class="sxs-lookup"><span data-stu-id="68927-105">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="68927-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="68927-106">Attributes and Elements</span></span>

<span data-ttu-id="68927-107">下列各節描述元素的屬性、子專案和父項目 `Label` 。</span><span class="sxs-lookup"><span data-stu-id="68927-107">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="68927-108">屬性</span><span class="sxs-lookup"><span data-stu-id="68927-108">Attributes</span></span>

<span data-ttu-id="68927-109">無。</span><span class="sxs-lookup"><span data-stu-id="68927-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="68927-110">子元素</span><span class="sxs-lookup"><span data-stu-id="68927-110">Child Elements</span></span>

<span data-ttu-id="68927-111">無。</span><span class="sxs-lookup"><span data-stu-id="68927-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="68927-112">父項目</span><span class="sxs-lookup"><span data-stu-id="68927-112">Parent Elements</span></span>

|<span data-ttu-id="68927-113">元素</span><span class="sxs-lookup"><span data-stu-id="68927-113">Element</span></span>|<span data-ttu-id="68927-114">描述</span><span class="sxs-lookup"><span data-stu-id="68927-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="68927-115">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="68927-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="68927-116">定義新群組物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="68927-116">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="68927-117">文字值</span><span class="sxs-lookup"><span data-stu-id="68927-117">Text Value</span></span>

<span data-ttu-id="68927-118">指定每當 Windows PowerShell 遇到新的屬性或腳本值時所顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="68927-118">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="68927-119">備註</span><span class="sxs-lookup"><span data-stu-id="68927-119">Remarks</span></span>

<span data-ttu-id="68927-120">除了此元素所指定的文字之外，Windows PowerShell 還會顯示啟動群組的新值，並在群組前後加上一個空白行。</span><span class="sxs-lookup"><span data-stu-id="68927-120">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="68927-121">範例</span><span class="sxs-lookup"><span data-stu-id="68927-121">Example</span></span>

<span data-ttu-id="68927-122">下列範例會顯示新群組的標籤。</span><span class="sxs-lookup"><span data-stu-id="68927-122">The following example shows the label for a new group.</span></span> <span data-ttu-id="68927-123">顯示的標籤看起來會像這樣：`Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="68927-123">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="68927-124">如需包含此元素的完整格式檔案範例，請參閱[Wide View (GroupBy) ](./wide-view-groupby.md)。</span><span class="sxs-lookup"><span data-stu-id="68927-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="68927-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68927-125">See Also</span></span>

[<span data-ttu-id="68927-126">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="68927-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="68927-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="68927-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
