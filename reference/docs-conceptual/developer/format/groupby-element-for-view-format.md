---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視的 GroupBy 元素 (格式)
description: 檢視的 GroupBy 元素 (格式)
ms.openlocfilehash: d8ca93a3b2c1490928885579919c07f5eb274cd8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652108"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="30dd4-103">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="30dd4-103">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="30dd4-104">定義如何顯示新的物件群組。</span><span class="sxs-lookup"><span data-stu-id="30dd4-104">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="30dd4-105">定義資料表、清單、寬或自訂控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="30dd4-105">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="30dd4-106">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) GroupBy 專案的格式 (</span><span class="sxs-lookup"><span data-stu-id="30dd4-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="30dd4-107">語法</span><span class="sxs-lookup"><span data-stu-id="30dd4-107">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="30dd4-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="30dd4-108">Attributes and Elements</span></span>

<span data-ttu-id="30dd4-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="30dd4-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="30dd4-110">屬性</span><span class="sxs-lookup"><span data-stu-id="30dd4-110">Attributes</span></span>

<span data-ttu-id="30dd4-111">無。</span><span class="sxs-lookup"><span data-stu-id="30dd4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="30dd4-112">子元素</span><span class="sxs-lookup"><span data-stu-id="30dd4-112">Child Elements</span></span>

|<span data-ttu-id="30dd4-113">元素</span><span class="sxs-lookup"><span data-stu-id="30dd4-113">Element</span></span>|<span data-ttu-id="30dd4-114">描述</span><span class="sxs-lookup"><span data-stu-id="30dd4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="30dd4-115">GroupBy 的 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="30dd4-115">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="30dd4-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="30dd4-116">Optional element.</span></span><br /><br /> <span data-ttu-id="30dd4-117">定義顯示新群組的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="30dd4-117">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="30dd4-118">GroupBy 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="30dd4-118">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="30dd4-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="30dd4-119">Optional element.</span></span><br /><br /> <span data-ttu-id="30dd4-120">指定用來顯示新群組的控制項名稱。</span><span class="sxs-lookup"><span data-stu-id="30dd4-120">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="30dd4-121">GroupBy 的標籤元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="30dd4-121">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="30dd4-122">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="30dd4-122">Optional element.</span></span><br /><br /> <span data-ttu-id="30dd4-123">指定當遇到新群組時所顯示的標籤。</span><span class="sxs-lookup"><span data-stu-id="30dd4-123">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="30dd4-124">GroupBy 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="30dd4-124">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="30dd4-125">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="30dd4-125">Optional element.</span></span><br /><br /> <span data-ttu-id="30dd4-126">指定每當新群組值變更時，就會啟動新群組的 .NET 屬性。</span><span class="sxs-lookup"><span data-stu-id="30dd4-126">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="30dd4-127">GroupBy 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="30dd4-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="30dd4-128">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="30dd4-128">Optional element.</span></span><br /><br /> <span data-ttu-id="30dd4-129">指定每當新群組值變更時，會啟動新群組的腳本。</span><span class="sxs-lookup"><span data-stu-id="30dd4-129">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="30dd4-130">父項目</span><span class="sxs-lookup"><span data-stu-id="30dd4-130">Parent Elements</span></span>

|<span data-ttu-id="30dd4-131">元素</span><span class="sxs-lookup"><span data-stu-id="30dd4-131">Element</span></span>|<span data-ttu-id="30dd4-132">描述</span><span class="sxs-lookup"><span data-stu-id="30dd4-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="30dd4-133">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="30dd4-133">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="30dd4-134">定義顯示一或多個 .NET 物件的視圖。</span><span class="sxs-lookup"><span data-stu-id="30dd4-134">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="30dd4-135">備註</span><span class="sxs-lookup"><span data-stu-id="30dd4-135">Remarks</span></span>

<span data-ttu-id="30dd4-136">定義如何顯示新的物件群組時，您必須指定將啟動新群組的屬性或腳本。不過，您不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="30dd4-136">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="30dd4-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30dd4-137">See Also</span></span>

[<span data-ttu-id="30dd4-138">GroupBy 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="30dd4-138">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="30dd4-139">GroupBy 的標籤元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="30dd4-139">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="30dd4-140">GroupBy 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="30dd4-140">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="30dd4-141">GroupBy 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="30dd4-141">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="30dd4-142">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="30dd4-142">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="30dd4-143">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="30dd4-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
