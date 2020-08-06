---
title: ListControl (格式的專案名稱的 PropertyName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9ee466d7f73e53b129f8d46f49a21549683bb32c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780826"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="90e7d-102">ListControl 之 ListItem 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="90e7d-102">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="90e7d-103">指定其值顯示在清單中的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="90e7d-103">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="90e7d-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListEntries 專案 (格式) ListEntry 專案 (格式) ListItems 元素 (格式) 專案名稱專案 (格式專案的) PropertyName 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="90e7d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="90e7d-105">語法</span><span class="sxs-lookup"><span data-stu-id="90e7d-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="90e7d-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="90e7d-106">Attributes and Elements</span></span>

<span data-ttu-id="90e7d-107">下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="90e7d-107">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="90e7d-108">屬性</span><span class="sxs-lookup"><span data-stu-id="90e7d-108">Attributes</span></span>

<span data-ttu-id="90e7d-109">無。</span><span class="sxs-lookup"><span data-stu-id="90e7d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="90e7d-110">子元素</span><span class="sxs-lookup"><span data-stu-id="90e7d-110">Child Elements</span></span>

<span data-ttu-id="90e7d-111">無。</span><span class="sxs-lookup"><span data-stu-id="90e7d-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="90e7d-112">父項目</span><span class="sxs-lookup"><span data-stu-id="90e7d-112">Parent Elements</span></span>

|<span data-ttu-id="90e7d-113">元素</span><span class="sxs-lookup"><span data-stu-id="90e7d-113">Element</span></span>|<span data-ttu-id="90e7d-114">描述</span><span class="sxs-lookup"><span data-stu-id="90e7d-114">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="90e7d-115">[ (格式的 [專案] 元素) ](./listitem-element-for-listitems-for-listcontrol-format.md)</span><span class="sxs-lookup"><span data-stu-id="90e7d-115">[ListItem Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)</span></span>|<span data-ttu-id="90e7d-116">定義屬性或腳本，其值會顯示在清單視圖的資料列中。</span><span class="sxs-lookup"><span data-stu-id="90e7d-116">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="90e7d-117">文字值</span><span class="sxs-lookup"><span data-stu-id="90e7d-117">Text Value</span></span>

<span data-ttu-id="90e7d-118">指定顯示其值的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="90e7d-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="90e7d-119">備註</span><span class="sxs-lookup"><span data-stu-id="90e7d-119">Remarks</span></span>

<span data-ttu-id="90e7d-120">當指定此元素時，您不能指定[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="90e7d-120">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="90e7d-121">除了顯示內容值之外，您也可以指定值的標籤，或可用於變更值顯示的格式字串。</span><span class="sxs-lookup"><span data-stu-id="90e7d-121">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="90e7d-122">如需在清單視圖中指定資料的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="90e7d-122">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="90e7d-123">範例</span><span class="sxs-lookup"><span data-stu-id="90e7d-123">Example</span></span>

<span data-ttu-id="90e7d-124">下列範例顯示如何指定其值顯示的標籤和屬性。</span><span class="sxs-lookup"><span data-stu-id="90e7d-124">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="90e7d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90e7d-125">See Also</span></span>

[<span data-ttu-id="90e7d-126">ListControl 之 ListItem 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="90e7d-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="90e7d-127">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="90e7d-127">Creating a List View</span></span>](./creating-a-list-view.md)

<span data-ttu-id="90e7d-128">[ListControl (格式的 [專案] 元素) ](./listitem-element-for-listitems-for-listcontrol-format.md)</span><span class="sxs-lookup"><span data-stu-id="90e7d-128">[ListItem Element for ListControl(Format)](./listitem-element-for-listitems-for-listcontrol-format.md)</span></span>

[<span data-ttu-id="90e7d-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="90e7d-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
