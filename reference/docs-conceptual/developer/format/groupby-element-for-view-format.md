---
title: View (格式) 的 GroupBy 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2f9071a3ebbc7cc2ccb7721dd518e82723e9cc4e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781421"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="68013-102">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="68013-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="68013-103">定義新群組物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="68013-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="68013-104">當定義資料表、清單、寬型或自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="68013-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="68013-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) GroupBy 元素以查看 (格式) </span><span class="sxs-lookup"><span data-stu-id="68013-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="68013-106">語法</span><span class="sxs-lookup"><span data-stu-id="68013-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="68013-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="68013-107">Attributes and Elements</span></span>

<span data-ttu-id="68013-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="68013-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="68013-109">屬性</span><span class="sxs-lookup"><span data-stu-id="68013-109">Attributes</span></span>

<span data-ttu-id="68013-110">無。</span><span class="sxs-lookup"><span data-stu-id="68013-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="68013-111">子元素</span><span class="sxs-lookup"><span data-stu-id="68013-111">Child Elements</span></span>

|<span data-ttu-id="68013-112">元素</span><span class="sxs-lookup"><span data-stu-id="68013-112">Element</span></span>|<span data-ttu-id="68013-113">描述</span><span class="sxs-lookup"><span data-stu-id="68013-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="68013-114">GroupBy 的 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="68013-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="68013-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="68013-115">Optional element.</span></span><br /><br /> <span data-ttu-id="68013-116">定義顯示新群組的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="68013-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="68013-117">GroupBy 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="68013-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="68013-118">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="68013-118">Optional element.</span></span><br /><br /> <span data-ttu-id="68013-119">指定用來顯示新群組之控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="68013-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="68013-120">GroupBy 的標籤元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="68013-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="68013-121">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="68013-121">Optional element.</span></span><br /><br /> <span data-ttu-id="68013-122">指定遇到新群組時所顯示的標籤。</span><span class="sxs-lookup"><span data-stu-id="68013-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="68013-123">GroupBy 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="68013-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="68013-124">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="68013-124">Optional element.</span></span><br /><br /> <span data-ttu-id="68013-125">指定 .NET 屬性，每當其值變更時，就會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="68013-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="68013-126">GroupBy 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="68013-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="68013-127">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="68013-127">Optional element.</span></span><br /><br /> <span data-ttu-id="68013-128">指定每當新群組的值變更時，就會啟動的腳本。</span><span class="sxs-lookup"><span data-stu-id="68013-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="68013-129">父項目</span><span class="sxs-lookup"><span data-stu-id="68013-129">Parent Elements</span></span>

|<span data-ttu-id="68013-130">元素</span><span class="sxs-lookup"><span data-stu-id="68013-130">Element</span></span>|<span data-ttu-id="68013-131">描述</span><span class="sxs-lookup"><span data-stu-id="68013-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="68013-132">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="68013-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="68013-133">定義顯示一或多個 .NET 物件的視圖。</span><span class="sxs-lookup"><span data-stu-id="68013-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="68013-134">備註</span><span class="sxs-lookup"><span data-stu-id="68013-134">Remarks</span></span>

<span data-ttu-id="68013-135">當定義新群組物件的顯示方式時，您必須指定將啟動新群組的屬性或腳本。不過，您不能同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="68013-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="68013-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68013-136">See Also</span></span>

[<span data-ttu-id="68013-137">GroupBy 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="68013-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="68013-138">GroupBy 的標籤元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="68013-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="68013-139">GroupBy 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="68013-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="68013-140">GroupBy 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="68013-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="68013-141">檢視元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="68013-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="68013-142">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="68013-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
