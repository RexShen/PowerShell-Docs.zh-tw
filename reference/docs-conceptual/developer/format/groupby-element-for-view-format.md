---
title: View 的 GroupBy 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363627"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="cca40-102">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="cca40-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="cca40-103">定義新群組物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="cca40-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="cca40-104">當定義資料表、清單、寬型或自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="cca40-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="cca40-105">設定元素（格式） ViewDefinitions 元素（格式） View 元素（格式） GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cca40-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cca40-106">語法</span><span class="sxs-lookup"><span data-stu-id="cca40-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cca40-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="cca40-107">Attributes and Elements</span></span>

<span data-ttu-id="cca40-108">下列各節說明屬性、子項目和父元素。</span><span class="sxs-lookup"><span data-stu-id="cca40-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="cca40-109">屬性</span><span class="sxs-lookup"><span data-stu-id="cca40-109">Attributes</span></span>

<span data-ttu-id="cca40-110">無。</span><span class="sxs-lookup"><span data-stu-id="cca40-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cca40-111">子元素</span><span class="sxs-lookup"><span data-stu-id="cca40-111">Child Elements</span></span>

|<span data-ttu-id="cca40-112">元素</span><span class="sxs-lookup"><span data-stu-id="cca40-112">Element</span></span>|<span data-ttu-id="cca40-113">描述</span><span class="sxs-lookup"><span data-stu-id="cca40-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cca40-114">GroupBy 的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cca40-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="cca40-115">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="cca40-115">Optional element.</span></span><br /><br /> <span data-ttu-id="cca40-116">定義顯示新群組的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="cca40-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="cca40-117">GroupBy 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cca40-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="cca40-118">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="cca40-118">Optional element.</span></span><br /><br /> <span data-ttu-id="cca40-119">指定用來顯示新群組之控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="cca40-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="cca40-120">GroupBy 的標籤元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cca40-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="cca40-121">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="cca40-121">Optional element.</span></span><br /><br /> <span data-ttu-id="cca40-122">指定遇到新群組時所顯示的標籤。</span><span class="sxs-lookup"><span data-stu-id="cca40-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="cca40-123">GroupBy 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cca40-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="cca40-124">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="cca40-124">Optional element.</span></span><br /><br /> <span data-ttu-id="cca40-125">指定 .NET 屬性，每當其值變更時，就會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="cca40-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="cca40-126">GroupBy 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cca40-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="cca40-127">選擇性元素。</span><span class="sxs-lookup"><span data-stu-id="cca40-127">Optional element.</span></span><br /><br /> <span data-ttu-id="cca40-128">指定每當新群組的值變更時，就會啟動的腳本。</span><span class="sxs-lookup"><span data-stu-id="cca40-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cca40-129">父元素</span><span class="sxs-lookup"><span data-stu-id="cca40-129">Parent Elements</span></span>

|<span data-ttu-id="cca40-130">元素</span><span class="sxs-lookup"><span data-stu-id="cca40-130">Element</span></span>|<span data-ttu-id="cca40-131">描述</span><span class="sxs-lookup"><span data-stu-id="cca40-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cca40-132">View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cca40-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="cca40-133">定義顯示一或多個 .NET 物件的視圖。</span><span class="sxs-lookup"><span data-stu-id="cca40-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cca40-134">備註</span><span class="sxs-lookup"><span data-stu-id="cca40-134">Remarks</span></span>

<span data-ttu-id="cca40-135">當定義新群組物件的顯示方式時，您必須指定將啟動新群組的屬性或腳本。不過，您不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="cca40-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="cca40-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cca40-136">See Also</span></span>

[<span data-ttu-id="cca40-137">GroupBy 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cca40-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="cca40-138">GroupBy 的標籤元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cca40-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="cca40-139">GroupBy 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cca40-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="cca40-140">GroupBy 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cca40-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="cca40-141">View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cca40-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="cca40-142">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="cca40-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
