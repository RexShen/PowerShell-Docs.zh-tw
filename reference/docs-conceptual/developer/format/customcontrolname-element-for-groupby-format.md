---
title: GroupBy 的 CustomControlName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368877"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="8a78a-102">GroupBy 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="8a78a-102">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="8a78a-103">指定用來顯示新群組的自訂控制項名稱。</span><span class="sxs-lookup"><span data-stu-id="8a78a-103">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="8a78a-104">定義資料表、清單、寬型或自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="8a78a-104">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="8a78a-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） groupby 元素（格式） GroupBy 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="8a78a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8a78a-106">語法</span><span class="sxs-lookup"><span data-stu-id="8a78a-106">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8a78a-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="8a78a-107">Attributes and Elements</span></span>

<span data-ttu-id="8a78a-108">下列各節說明 `CustomControlName` 元素的屬性、子專案和父元素。</span><span class="sxs-lookup"><span data-stu-id="8a78a-108">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8a78a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="8a78a-109">Attributes</span></span>

<span data-ttu-id="8a78a-110">無。</span><span class="sxs-lookup"><span data-stu-id="8a78a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8a78a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="8a78a-111">Child Elements</span></span>

<span data-ttu-id="8a78a-112">無。</span><span class="sxs-lookup"><span data-stu-id="8a78a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8a78a-113">父元素</span><span class="sxs-lookup"><span data-stu-id="8a78a-113">Parent Elements</span></span>

|<span data-ttu-id="8a78a-114">元素</span><span class="sxs-lookup"><span data-stu-id="8a78a-114">Element</span></span>|<span data-ttu-id="8a78a-115">描述</span><span class="sxs-lookup"><span data-stu-id="8a78a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8a78a-116">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="8a78a-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="8a78a-117">定義 Windows PowerShell 如何顯示新的物件群組。</span><span class="sxs-lookup"><span data-stu-id="8a78a-117">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8a78a-118">文字值</span><span class="sxs-lookup"><span data-stu-id="8a78a-118">Text Value</span></span>

<span data-ttu-id="8a78a-119">指定用來顯示新群組的自訂控制項名稱。</span><span class="sxs-lookup"><span data-stu-id="8a78a-119">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="8a78a-120">備註</span><span class="sxs-lookup"><span data-stu-id="8a78a-120">Remarks</span></span>

<span data-ttu-id="8a78a-121">您可以建立可供格式化檔案的所有視圖使用的通用控制項，而且可以建立可供特定視圖使用的 view 控制項。</span><span class="sxs-lookup"><span data-stu-id="8a78a-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="8a78a-122">下列元素會指定這些自訂控制項的名稱：</span><span class="sxs-lookup"><span data-stu-id="8a78a-122">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="8a78a-123">設定之控制項的控制項的名稱元素（格式）</span><span class="sxs-lookup"><span data-stu-id="8a78a-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="8a78a-124">View 控制項控制項的 Name 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="8a78a-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="8a78a-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a78a-125">See Also</span></span>

[<span data-ttu-id="8a78a-126">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="8a78a-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="8a78a-127">設定之控制項的控制項的名稱元素（格式）</span><span class="sxs-lookup"><span data-stu-id="8a78a-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="8a78a-128">View 控制項控制項的 Name 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="8a78a-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="8a78a-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="8a78a-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
