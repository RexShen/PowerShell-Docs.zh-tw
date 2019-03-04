---
title: 檢視 （格式） 的 GroupBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859524"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="6bd73-102">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="6bd73-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="6bd73-103">定義新的一整組物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="6bd73-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="6bd73-104">定義資料表、 清單、 寬，或自訂的控制項檢視時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="6bd73-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="6bd73-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目進行檢視 （格式）</span><span class="sxs-lookup"><span data-stu-id="6bd73-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6bd73-106">語法</span><span class="sxs-lookup"><span data-stu-id="6bd73-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6bd73-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="6bd73-107">Attributes and Elements</span></span>

<span data-ttu-id="6bd73-108">下列各節說明屬性、 子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6bd73-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6bd73-109">屬性</span><span class="sxs-lookup"><span data-stu-id="6bd73-109">Attributes</span></span>

<span data-ttu-id="6bd73-110">無。</span><span class="sxs-lookup"><span data-stu-id="6bd73-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6bd73-111">子元素</span><span class="sxs-lookup"><span data-stu-id="6bd73-111">Child Elements</span></span>

|<span data-ttu-id="6bd73-112">元素</span><span class="sxs-lookup"><span data-stu-id="6bd73-112">Element</span></span>|<span data-ttu-id="6bd73-113">描述</span><span class="sxs-lookup"><span data-stu-id="6bd73-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6bd73-114">CustomControl GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="6bd73-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="6bd73-115">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="6bd73-115">Optional element.</span></span><br /><br /> <span data-ttu-id="6bd73-116">定義自訂控制項，顯示新的群組。</span><span class="sxs-lookup"><span data-stu-id="6bd73-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="6bd73-117">CustomControlName GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="6bd73-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="6bd73-118">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="6bd73-118">Optional element.</span></span><br /><br /> <span data-ttu-id="6bd73-119">指定用來顯示新的群組控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="6bd73-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="6bd73-120">GroupBy （格式） 的 label 項目</span><span class="sxs-lookup"><span data-stu-id="6bd73-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="6bd73-121">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="6bd73-121">Optional element.</span></span><br /><br /> <span data-ttu-id="6bd73-122">指定在發現新的群組時，會顯示的標籤。</span><span class="sxs-lookup"><span data-stu-id="6bd73-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="6bd73-123">GroupBy （格式） 的屬性名稱項目</span><span class="sxs-lookup"><span data-stu-id="6bd73-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="6bd73-124">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="6bd73-124">Optional element.</span></span><br /><br /> <span data-ttu-id="6bd73-125">指定.NET 屬性在啟動新的群組，其值變更時。</span><span class="sxs-lookup"><span data-stu-id="6bd73-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="6bd73-126">GroupBy （格式） 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="6bd73-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="6bd73-127">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="6bd73-127">Optional element.</span></span><br /><br /> <span data-ttu-id="6bd73-128">指定的指令碼，其值變更時，會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="6bd73-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6bd73-129">父元素</span><span class="sxs-lookup"><span data-stu-id="6bd73-129">Parent Elements</span></span>

|<span data-ttu-id="6bd73-130">元素</span><span class="sxs-lookup"><span data-stu-id="6bd73-130">Element</span></span>|<span data-ttu-id="6bd73-131">描述</span><span class="sxs-lookup"><span data-stu-id="6bd73-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6bd73-132">檢視項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="6bd73-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="6bd73-133">定義顯示一或多個.NET 物件的檢視。</span><span class="sxs-lookup"><span data-stu-id="6bd73-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6bd73-134">備註</span><span class="sxs-lookup"><span data-stu-id="6bd73-134">Remarks</span></span>

<span data-ttu-id="6bd73-135">在定義新的群組物件的顯示方式時，您必須指定屬性或指令碼會啟動新的群組;不過，您無法同時指定。</span><span class="sxs-lookup"><span data-stu-id="6bd73-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="6bd73-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bd73-136">See Also</span></span>

[<span data-ttu-id="6bd73-137">CustomControlName GroupBy （格式） 的項目</span><span class="sxs-lookup"><span data-stu-id="6bd73-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="6bd73-138">GroupBy （格式） 的 label 項目</span><span class="sxs-lookup"><span data-stu-id="6bd73-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="6bd73-139">GroupBy （格式） 的屬性名稱項目</span><span class="sxs-lookup"><span data-stu-id="6bd73-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="6bd73-140">GroupBy （格式） 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="6bd73-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="6bd73-141">檢視項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="6bd73-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="6bd73-142">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="6bd73-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
