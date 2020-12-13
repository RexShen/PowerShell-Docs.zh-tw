---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 ListEntry 的 ListItems 元素 (格式)
description: ListControl 之 ListEntry 的 ListItems 元素 (格式)
ms.openlocfilehash: 1553c81bc559020223a3c1fea10336baf017c9a0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666530"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="0b67e-103">ListControl 之 ListEntry 的 ListItems 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0b67e-103">ListItems Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="0b67e-104">定義屬性和腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="0b67e-104">Defines the properties and scripts whose values are displayed in the rows of the list view.</span></span>

<span data-ttu-id="0b67e-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListEntries 元素用於清單控制項 (格式) ListControl (格式) ListItems 專案 (格式) </span><span class="sxs-lookup"><span data-stu-id="0b67e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for List Control (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0b67e-106">語法</span><span class="sxs-lookup"><span data-stu-id="0b67e-106">Syntax</span></span>

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0b67e-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0b67e-107">Attributes and Elements</span></span>

<span data-ttu-id="0b67e-108">下列各節描述專案的屬性、子項目和父元素 `ListItems` 。</span><span class="sxs-lookup"><span data-stu-id="0b67e-108">The following sections describe the attributes, child elements, and parent element of the `ListItems` element.</span></span> <span data-ttu-id="0b67e-109">可指定的子專案數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="0b67e-109">There is no limit to the number of child elements that can be specified.</span></span> <span data-ttu-id="0b67e-110">子項目的順序會定義值顯示在清單視圖中的順序。</span><span class="sxs-lookup"><span data-stu-id="0b67e-110">The order of the child elements defines the order that values are displayed in the list view.</span></span>

### <a name="attributes"></a><span data-ttu-id="0b67e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0b67e-111">Attributes</span></span>

<span data-ttu-id="0b67e-112">無。</span><span class="sxs-lookup"><span data-stu-id="0b67e-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0b67e-113">子元素</span><span class="sxs-lookup"><span data-stu-id="0b67e-113">Child Elements</span></span>

|<span data-ttu-id="0b67e-114">元素</span><span class="sxs-lookup"><span data-stu-id="0b67e-114">Element</span></span>|<span data-ttu-id="0b67e-115">描述</span><span class="sxs-lookup"><span data-stu-id="0b67e-115">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="0b67e-116">[ListControl (格式的 [專案] 元素) ](./listitem-element-for-listitems-for-listcontrol-format.md)</span><span class="sxs-lookup"><span data-stu-id="0b67e-116">[ListItem Element for ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)</span></span>|<span data-ttu-id="0b67e-117">必要元素。</span><span class="sxs-lookup"><span data-stu-id="0b67e-117">Required element.</span></span><br /><br /> <span data-ttu-id="0b67e-118">定義清單視圖顯示其值的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="0b67e-118">Defines the property or script whose value is displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0b67e-119">父項目</span><span class="sxs-lookup"><span data-stu-id="0b67e-119">Parent Elements</span></span>

|<span data-ttu-id="0b67e-120">元素</span><span class="sxs-lookup"><span data-stu-id="0b67e-120">Element</span></span>|<span data-ttu-id="0b67e-121">描述</span><span class="sxs-lookup"><span data-stu-id="0b67e-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0b67e-122">ListControl 的 ListEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0b67e-122">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="0b67e-123">提供清單視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="0b67e-123">Provides a definition of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0b67e-124">備註</span><span class="sxs-lookup"><span data-stu-id="0b67e-124">Remarks</span></span>

<span data-ttu-id="0b67e-125">如需這種檢視類型的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="0b67e-125">For more information about this type of view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0b67e-126">範例</span><span class="sxs-lookup"><span data-stu-id="0b67e-126">Example</span></span>

<span data-ttu-id="0b67e-127">這個範例會示範定義清單視圖之三個數據列的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="0b67e-127">This example shows the XML elements that define three rows of the list view.</span></span>

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="0b67e-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b67e-128">See Also</span></span>

[<span data-ttu-id="0b67e-129">ListControl 的 ListEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0b67e-129">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

<span data-ttu-id="0b67e-130">[ListControl (格式的 [專案] 元素) ](./listitem-element-for-listitems-for-listcontrol-format.md)</span><span class="sxs-lookup"><span data-stu-id="0b67e-130">[ListItem Element for ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)</span></span>

[<span data-ttu-id="0b67e-131">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="0b67e-131">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="0b67e-132">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="0b67e-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
