---
title: ListControl (格式) 的 ScriptBlock 元素Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 249d3e36b4246b7baa410815122f8e30340f1862
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785450"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="e7e51-102">ListControl 之 ListItem 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e7e51-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="e7e51-103">指定其值顯示在資料列中的腳本。</span><span class="sxs-lookup"><span data-stu-id="e7e51-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="e7e51-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListControl (格式) ListEntry 元素（ListEntries for ListControl (format) ListItems 元素 (ListEntry for ListControl) format (ScriptBlock 元素用於 ListItems) 格式的 ListEntries</span><span class="sxs-lookup"><span data-stu-id="e7e51-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e7e51-105">語法</span><span class="sxs-lookup"><span data-stu-id="e7e51-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e7e51-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e7e51-106">Attributes and Elements</span></span>

<span data-ttu-id="e7e51-107">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="e7e51-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e7e51-108">屬性</span><span class="sxs-lookup"><span data-stu-id="e7e51-108">Attributes</span></span>

<span data-ttu-id="e7e51-109">無。</span><span class="sxs-lookup"><span data-stu-id="e7e51-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e7e51-110">子元素</span><span class="sxs-lookup"><span data-stu-id="e7e51-110">Child Elements</span></span>

<span data-ttu-id="e7e51-111">無。</span><span class="sxs-lookup"><span data-stu-id="e7e51-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e7e51-112">父項目</span><span class="sxs-lookup"><span data-stu-id="e7e51-112">Parent Elements</span></span>

|<span data-ttu-id="e7e51-113">元素</span><span class="sxs-lookup"><span data-stu-id="e7e51-113">Element</span></span>|<span data-ttu-id="e7e51-114">描述</span><span class="sxs-lookup"><span data-stu-id="e7e51-114">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="e7e51-115">[ (格式的 [專案] 元素) ](./listitem-element-for-listitems-for-listcontrol-format.md)</span><span class="sxs-lookup"><span data-stu-id="e7e51-115">[ListItem Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)</span></span>|<span data-ttu-id="e7e51-116">定義屬性或腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="e7e51-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e7e51-117">文字值</span><span class="sxs-lookup"><span data-stu-id="e7e51-117">Text Value</span></span>

<span data-ttu-id="e7e51-118">指定其值顯示在資料列中的腳本。</span><span class="sxs-lookup"><span data-stu-id="e7e51-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="e7e51-119">備註</span><span class="sxs-lookup"><span data-stu-id="e7e51-119">Remarks</span></span>

<span data-ttu-id="e7e51-120">當指定此元素時，您無法指定[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="e7e51-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="e7e51-121">如需在清單視圖中指定腳本的詳細資訊，請參閱[清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="e7e51-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e7e51-122">範例</span><span class="sxs-lookup"><span data-stu-id="e7e51-122">Example</span></span>

<span data-ttu-id="e7e51-123">下列範例顯示如何指定屬性，其值會顯示。</span><span class="sxs-lookup"><span data-stu-id="e7e51-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="e7e51-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7e51-124">See Also</span></span>

[<span data-ttu-id="e7e51-125">ListControl 之 ListItem 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e7e51-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="e7e51-126">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="e7e51-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e7e51-127">ListControl 之 ListItems 的 ListItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e7e51-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="e7e51-128">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="e7e51-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
