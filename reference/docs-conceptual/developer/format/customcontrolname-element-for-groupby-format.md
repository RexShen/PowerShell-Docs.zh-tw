---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 的 CustomControlName 元素 (格式)
description: GroupBy 的 CustomControlName 元素 (格式)
ms.openlocfilehash: 03664fe4d5559312e2720a3892493c90c15f7501
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655417"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="4def7-103">GroupBy 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4def7-103">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="4def7-104">指定用來顯示新群組的自訂控制項名稱。</span><span class="sxs-lookup"><span data-stu-id="4def7-104">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="4def7-105">定義資料表、清單、寬或自訂控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="4def7-105">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="4def7-106">ViewDefinitions 元素格式的設定元素 (格式) 元素 (格式) View 元素 (格式) groupby (格式) groupby 的元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="4def7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4def7-107">語法</span><span class="sxs-lookup"><span data-stu-id="4def7-107">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4def7-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4def7-108">Attributes and Elements</span></span>

<span data-ttu-id="4def7-109">下列各節描述專案的屬性、子項目和父元素 `CustomControlName` 。</span><span class="sxs-lookup"><span data-stu-id="4def7-109">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4def7-110">屬性</span><span class="sxs-lookup"><span data-stu-id="4def7-110">Attributes</span></span>

<span data-ttu-id="4def7-111">無。</span><span class="sxs-lookup"><span data-stu-id="4def7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4def7-112">子元素</span><span class="sxs-lookup"><span data-stu-id="4def7-112">Child Elements</span></span>

<span data-ttu-id="4def7-113">無。</span><span class="sxs-lookup"><span data-stu-id="4def7-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4def7-114">父項目</span><span class="sxs-lookup"><span data-stu-id="4def7-114">Parent Elements</span></span>

|<span data-ttu-id="4def7-115">元素</span><span class="sxs-lookup"><span data-stu-id="4def7-115">Element</span></span>|<span data-ttu-id="4def7-116">描述</span><span class="sxs-lookup"><span data-stu-id="4def7-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4def7-117">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4def7-117">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="4def7-118">定義 Windows PowerShell 如何顯示新的物件群組。</span><span class="sxs-lookup"><span data-stu-id="4def7-118">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4def7-119">文字值</span><span class="sxs-lookup"><span data-stu-id="4def7-119">Text Value</span></span>

<span data-ttu-id="4def7-120">指定用來顯示新群組的自訂控制項名稱。</span><span class="sxs-lookup"><span data-stu-id="4def7-120">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="4def7-121">備註</span><span class="sxs-lookup"><span data-stu-id="4def7-121">Remarks</span></span>

<span data-ttu-id="4def7-122">您可以建立可供格式化檔案的所有視圖使用的通用控制項，也可以建立可供特定視圖使用的 view 控制項。</span><span class="sxs-lookup"><span data-stu-id="4def7-122">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="4def7-123">下列元素會指定這些自訂控制項的名稱：</span><span class="sxs-lookup"><span data-stu-id="4def7-123">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="4def7-124">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4def7-124">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="4def7-125">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4def7-125">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="4def7-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4def7-126">See Also</span></span>

[<span data-ttu-id="4def7-127">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4def7-127">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="4def7-128">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4def7-128">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="4def7-129">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4def7-129">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="4def7-130">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="4def7-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
