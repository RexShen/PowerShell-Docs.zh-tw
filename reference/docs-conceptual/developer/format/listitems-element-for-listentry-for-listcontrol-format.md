---
title: ListControl (格式) 的 ListEntry 的 ListItems 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 03b89a3df2ab0498533d0c00f303f643e0039b25
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781132"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="d258e-102">ListControl 之 ListEntry 的 ListItems 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d258e-102">ListItems Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="d258e-103">定義屬性和腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="d258e-103">Defines the properties and scripts whose values are displayed in the rows of the list view.</span></span>

<span data-ttu-id="d258e-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) ListControl 元素 (format) ListEntry 元素 for ListControl (format) ListItems 元素 for ListControl (Format) </span><span class="sxs-lookup"><span data-stu-id="d258e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for List Control (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d258e-105">語法</span><span class="sxs-lookup"><span data-stu-id="d258e-105">Syntax</span></span>

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d258e-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d258e-106">Attributes and Elements</span></span>

<span data-ttu-id="d258e-107">下列各節描述元素的屬性、子專案和父項目 `ListItems` 。</span><span class="sxs-lookup"><span data-stu-id="d258e-107">The following sections describe the attributes, child elements, and parent element of the `ListItems` element.</span></span> <span data-ttu-id="d258e-108">可以指定的子項目數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="d258e-108">There is no limit to the number of child elements that can be specified.</span></span> <span data-ttu-id="d258e-109">子專案的順序會定義在清單視圖中顯示值的順序。</span><span class="sxs-lookup"><span data-stu-id="d258e-109">The order of the child elements defines the order that values are displayed in the list view.</span></span>

### <a name="attributes"></a><span data-ttu-id="d258e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d258e-110">Attributes</span></span>

<span data-ttu-id="d258e-111">無。</span><span class="sxs-lookup"><span data-stu-id="d258e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d258e-112">子元素</span><span class="sxs-lookup"><span data-stu-id="d258e-112">Child Elements</span></span>

|<span data-ttu-id="d258e-113">元素</span><span class="sxs-lookup"><span data-stu-id="d258e-113">Element</span></span>|<span data-ttu-id="d258e-114">描述</span><span class="sxs-lookup"><span data-stu-id="d258e-114">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="d258e-115">[ListControl (格式的 [專案] 元素) ](./listitem-element-for-listitems-for-listcontrol-format.md)</span><span class="sxs-lookup"><span data-stu-id="d258e-115">[ListItem Element for ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)</span></span>|<span data-ttu-id="d258e-116">必要元素。</span><span class="sxs-lookup"><span data-stu-id="d258e-116">Required element.</span></span><br /><br /> <span data-ttu-id="d258e-117">定義清單視圖會顯示其值的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="d258e-117">Defines the property or script whose value is displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d258e-118">父項目</span><span class="sxs-lookup"><span data-stu-id="d258e-118">Parent Elements</span></span>

|<span data-ttu-id="d258e-119">元素</span><span class="sxs-lookup"><span data-stu-id="d258e-119">Element</span></span>|<span data-ttu-id="d258e-120">描述</span><span class="sxs-lookup"><span data-stu-id="d258e-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d258e-121">ListControl 的 ListEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d258e-121">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="d258e-122">提供清單視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="d258e-122">Provides a definition of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d258e-123">備註</span><span class="sxs-lookup"><span data-stu-id="d258e-123">Remarks</span></span>

<span data-ttu-id="d258e-124">如需這種檢視類型的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d258e-124">For more information about this type of view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d258e-125">範例</span><span class="sxs-lookup"><span data-stu-id="d258e-125">Example</span></span>

<span data-ttu-id="d258e-126">這個範例會顯示定義清單視圖之三個數據列的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="d258e-126">This example shows the XML elements that define three rows of the list view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d258e-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d258e-127">See Also</span></span>

[<span data-ttu-id="d258e-128">ListControl 的 ListEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d258e-128">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

<span data-ttu-id="d258e-129">[ListControl (格式的 [專案] 元素) ](./listitem-element-for-listitems-for-listcontrol-format.md)</span><span class="sxs-lookup"><span data-stu-id="d258e-129">[ListItem Element for ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)</span></span>

[<span data-ttu-id="d258e-130">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="d258e-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d258e-131">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="d258e-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
