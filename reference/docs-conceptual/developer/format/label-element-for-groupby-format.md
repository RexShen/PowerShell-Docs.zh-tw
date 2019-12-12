---
title: GroupBy 的標籤元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365197"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="ae16f-102">GroupBy 的標籤元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ae16f-102">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="ae16f-103">指定遇到新群組時所顯示的標籤。</span><span class="sxs-lookup"><span data-stu-id="ae16f-103">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="ae16f-104">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） groupby 元素（格式） GroupBy 專案（格式）</span><span class="sxs-lookup"><span data-stu-id="ae16f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ae16f-105">語法</span><span class="sxs-lookup"><span data-stu-id="ae16f-105">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ae16f-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="ae16f-106">Attributes and Elements</span></span>

<span data-ttu-id="ae16f-107">下列各節描述 `Label` 專案的屬性、子專案和父項目。</span><span class="sxs-lookup"><span data-stu-id="ae16f-107">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ae16f-108">屬性</span><span class="sxs-lookup"><span data-stu-id="ae16f-108">Attributes</span></span>

<span data-ttu-id="ae16f-109">無。</span><span class="sxs-lookup"><span data-stu-id="ae16f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ae16f-110">子元素</span><span class="sxs-lookup"><span data-stu-id="ae16f-110">Child Elements</span></span>

<span data-ttu-id="ae16f-111">無。</span><span class="sxs-lookup"><span data-stu-id="ae16f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ae16f-112">父元素</span><span class="sxs-lookup"><span data-stu-id="ae16f-112">Parent Elements</span></span>

|<span data-ttu-id="ae16f-113">元素</span><span class="sxs-lookup"><span data-stu-id="ae16f-113">Element</span></span>|<span data-ttu-id="ae16f-114">描述</span><span class="sxs-lookup"><span data-stu-id="ae16f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ae16f-115">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ae16f-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="ae16f-116">定義新群組物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="ae16f-116">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ae16f-117">文字值</span><span class="sxs-lookup"><span data-stu-id="ae16f-117">Text Value</span></span>

<span data-ttu-id="ae16f-118">指定每當 Windows PowerShell 遇到新的屬性或腳本值時所顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="ae16f-118">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="ae16f-119">備註</span><span class="sxs-lookup"><span data-stu-id="ae16f-119">Remarks</span></span>

<span data-ttu-id="ae16f-120">除了此元素所指定的文字之外，Windows PowerShell 還會顯示啟動群組的新值，並在群組前後加上一個空白行。</span><span class="sxs-lookup"><span data-stu-id="ae16f-120">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="ae16f-121">範例</span><span class="sxs-lookup"><span data-stu-id="ae16f-121">Example</span></span>

<span data-ttu-id="ae16f-122">下列範例會顯示新群組的標籤。</span><span class="sxs-lookup"><span data-stu-id="ae16f-122">The following example shows the label for a new group.</span></span> <span data-ttu-id="ae16f-123">顯示的標籤看起來會像這樣： `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="ae16f-123">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="ae16f-124">如需包含此元素之完整格式檔案的範例，請參閱[寬視圖（GroupBy）](./wide-view-groupby.md)。</span><span class="sxs-lookup"><span data-stu-id="ae16f-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ae16f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae16f-125">See Also</span></span>

[<span data-ttu-id="ae16f-126">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ae16f-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="ae16f-127">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="ae16f-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
