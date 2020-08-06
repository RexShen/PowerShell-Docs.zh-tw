---
title: ListControl (格式之專案的標籤元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ad80cc0478e7567b12d264ab661d843248ba48e1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783631"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="05a03-102">ListControl 之 ListItem 的標籤元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="05a03-102">Label Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="05a03-103">指定顯示在資料列中屬性或腳本值左邊的標籤。</span><span class="sxs-lookup"><span data-stu-id="05a03-103">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>

<span data-ttu-id="05a03-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListControl (格式) ListEntry 元素 ListControl (格式) ListItems 專案（ListEntry 的 ListControl 專案 () Label 元素，ListItems (格式的 ListEntries 的標籤) 格式 (</span><span class="sxs-lookup"><span data-stu-id="05a03-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems for ListEntry for ListControl Element (Format) ListItem Element for ListItems for ListControl (Format) Label Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="05a03-105">語法</span><span class="sxs-lookup"><span data-stu-id="05a03-105">Syntax</span></span>

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="05a03-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="05a03-106">Attributes and Elements</span></span>

<span data-ttu-id="05a03-107">下列各節說明屬性、子專案和元素的父元素 `Label` 。</span><span class="sxs-lookup"><span data-stu-id="05a03-107">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="05a03-108">屬性</span><span class="sxs-lookup"><span data-stu-id="05a03-108">Attributes</span></span>

<span data-ttu-id="05a03-109">無。</span><span class="sxs-lookup"><span data-stu-id="05a03-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="05a03-110">子元素</span><span class="sxs-lookup"><span data-stu-id="05a03-110">Child Elements</span></span>

<span data-ttu-id="05a03-111">無。</span><span class="sxs-lookup"><span data-stu-id="05a03-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="05a03-112">父項目</span><span class="sxs-lookup"><span data-stu-id="05a03-112">Parent Elements</span></span>

|<span data-ttu-id="05a03-113">元素</span><span class="sxs-lookup"><span data-stu-id="05a03-113">Element</span></span>|<span data-ttu-id="05a03-114">描述</span><span class="sxs-lookup"><span data-stu-id="05a03-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="05a03-115">ListControl 之 ListItems 的 ListItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="05a03-115">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="05a03-116">定義屬性或腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="05a03-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="05a03-117">文字值</span><span class="sxs-lookup"><span data-stu-id="05a03-117">Text Value</span></span>

<span data-ttu-id="05a03-118">指定要在屬性或腳本值左邊顯示的標籤。</span><span class="sxs-lookup"><span data-stu-id="05a03-118">Specify the label to be display to the left of the property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="05a03-119">備註</span><span class="sxs-lookup"><span data-stu-id="05a03-119">Remarks</span></span>

<span data-ttu-id="05a03-120">如果未指定標籤，則會顯示內容或腳本的名稱。</span><span class="sxs-lookup"><span data-stu-id="05a03-120">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="05a03-121">如需在清單視圖中使用標籤的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="05a03-121">For more information about using labels in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="05a03-122">範例</span><span class="sxs-lookup"><span data-stu-id="05a03-122">Example</span></span>

<span data-ttu-id="05a03-123">下列範例顯示如何將標籤加入至資料列。</span><span class="sxs-lookup"><span data-stu-id="05a03-123">The following example shows how to add a label to a row.</span></span>

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="05a03-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05a03-124">See Also</span></span>

[<span data-ttu-id="05a03-125">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="05a03-125">Creating a List View</span></span>](./creating-a-list-view.md)

<span data-ttu-id="05a03-126">[ (格式的 [專案] 元素) ](./listitem-element-for-listitems-for-listcontrol-format.md)</span><span class="sxs-lookup"><span data-stu-id="05a03-126">[ListItem Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)</span></span>

[<span data-ttu-id="05a03-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="05a03-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
