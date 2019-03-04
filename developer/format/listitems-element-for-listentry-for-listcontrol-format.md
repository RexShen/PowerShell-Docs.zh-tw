---
title: ListControl （格式） 的 ListEntry ListItems 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858584"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="50ae1-102">ListControl 之 ListEntry 的 ListItems 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="50ae1-102">ListItems Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="50ae1-103">定義屬性和其值會顯示在清單檢視的資料列中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="50ae1-103">Defines the properties and scripts whose values are displayed in the rows of the list view.</span></span>

<span data-ttu-id="50ae1-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 ListControl （格式） 的 ListControl （格式） ListItems 元素的清單控制項 （格式） ListEntry 項目</span><span class="sxs-lookup"><span data-stu-id="50ae1-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for List Control (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="50ae1-105">語法</span><span class="sxs-lookup"><span data-stu-id="50ae1-105">Syntax</span></span>

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="50ae1-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="50ae1-106">Attributes and Elements</span></span>

<span data-ttu-id="50ae1-107">下列各節說明屬性、 子項目和父項目`ListItems`項目。</span><span class="sxs-lookup"><span data-stu-id="50ae1-107">The following sections describe the attributes, child elements, and parent element of the `ListItems` element.</span></span> <span data-ttu-id="50ae1-108">沒有任何限制，您可以指定的子項目數目。</span><span class="sxs-lookup"><span data-stu-id="50ae1-108">There is no limit to the number of child elements that can be specified.</span></span> <span data-ttu-id="50ae1-109">子元素的順序定義的值會顯示在清單檢視中的順序。</span><span class="sxs-lookup"><span data-stu-id="50ae1-109">The order of the child elements defines the order that values are displayed in the list view.</span></span>

### <a name="attributes"></a><span data-ttu-id="50ae1-110">屬性</span><span class="sxs-lookup"><span data-stu-id="50ae1-110">Attributes</span></span>

<span data-ttu-id="50ae1-111">無。</span><span class="sxs-lookup"><span data-stu-id="50ae1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="50ae1-112">子元素</span><span class="sxs-lookup"><span data-stu-id="50ae1-112">Child Elements</span></span>

|<span data-ttu-id="50ae1-113">元素</span><span class="sxs-lookup"><span data-stu-id="50ae1-113">Element</span></span>|<span data-ttu-id="50ae1-114">描述</span><span class="sxs-lookup"><span data-stu-id="50ae1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="50ae1-115">ListControl （格式） 的 ListItem 項目</span><span class="sxs-lookup"><span data-stu-id="50ae1-115">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="50ae1-116">必要項目。</span><span class="sxs-lookup"><span data-stu-id="50ae1-116">Required element.</span></span><br /><br /> <span data-ttu-id="50ae1-117">定義屬性或其值會顯示 [清單] 檢視的指令碼。</span><span class="sxs-lookup"><span data-stu-id="50ae1-117">Defines the property or script whose value is displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="50ae1-118">父元素</span><span class="sxs-lookup"><span data-stu-id="50ae1-118">Parent Elements</span></span>

|<span data-ttu-id="50ae1-119">元素</span><span class="sxs-lookup"><span data-stu-id="50ae1-119">Element</span></span>|<span data-ttu-id="50ae1-120">描述</span><span class="sxs-lookup"><span data-stu-id="50ae1-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="50ae1-121">ListEntry ListControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="50ae1-121">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="50ae1-122">提供清單檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="50ae1-122">Provides a definition of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="50ae1-123">備註</span><span class="sxs-lookup"><span data-stu-id="50ae1-123">Remarks</span></span>

<span data-ttu-id="50ae1-124">如需這種檢視類型的詳細資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="50ae1-124">For more information about this type of view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="50ae1-125">範例</span><span class="sxs-lookup"><span data-stu-id="50ae1-125">Example</span></span>

<span data-ttu-id="50ae1-126">這個範例示範定義清單檢視的三個資料列的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="50ae1-126">This example shows the XML elements that define three rows of the list view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="50ae1-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50ae1-127">See Also</span></span>

[<span data-ttu-id="50ae1-128">ListEntry ListControl （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="50ae1-128">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="50ae1-129">ListControl （格式） 的 ListItem 項目</span><span class="sxs-lookup"><span data-stu-id="50ae1-129">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="50ae1-130">建立清單檢視</span><span class="sxs-lookup"><span data-stu-id="50ae1-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="50ae1-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="50ae1-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
