---
title: GroupBy (格式) 的 CustomControlName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4e3102f12cd37fa72a2de1bf1db5d1f82db31222
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783733"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="a3de1-102">GroupBy 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a3de1-102">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="a3de1-103">指定用來顯示新群組的自訂控制項名稱。</span><span class="sxs-lookup"><span data-stu-id="a3de1-103">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="a3de1-104">定義資料表、清單、寬型或自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="a3de1-104">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="a3de1-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素（GroupBy (格式）) CustomControlName 元素 (</span><span class="sxs-lookup"><span data-stu-id="a3de1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a3de1-106">語法</span><span class="sxs-lookup"><span data-stu-id="a3de1-106">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a3de1-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a3de1-107">Attributes and Elements</span></span>

<span data-ttu-id="a3de1-108">下列各節描述元素的屬性、子專案和父項目 `CustomControlName` 。</span><span class="sxs-lookup"><span data-stu-id="a3de1-108">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a3de1-109">屬性</span><span class="sxs-lookup"><span data-stu-id="a3de1-109">Attributes</span></span>

<span data-ttu-id="a3de1-110">無。</span><span class="sxs-lookup"><span data-stu-id="a3de1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a3de1-111">子元素</span><span class="sxs-lookup"><span data-stu-id="a3de1-111">Child Elements</span></span>

<span data-ttu-id="a3de1-112">無。</span><span class="sxs-lookup"><span data-stu-id="a3de1-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a3de1-113">父項目</span><span class="sxs-lookup"><span data-stu-id="a3de1-113">Parent Elements</span></span>

|<span data-ttu-id="a3de1-114">元素</span><span class="sxs-lookup"><span data-stu-id="a3de1-114">Element</span></span>|<span data-ttu-id="a3de1-115">描述</span><span class="sxs-lookup"><span data-stu-id="a3de1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a3de1-116">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a3de1-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="a3de1-117">定義 Windows PowerShell 如何顯示新的物件群組。</span><span class="sxs-lookup"><span data-stu-id="a3de1-117">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a3de1-118">文字值</span><span class="sxs-lookup"><span data-stu-id="a3de1-118">Text Value</span></span>

<span data-ttu-id="a3de1-119">指定用來顯示新群組的自訂控制項名稱。</span><span class="sxs-lookup"><span data-stu-id="a3de1-119">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="a3de1-120">備註</span><span class="sxs-lookup"><span data-stu-id="a3de1-120">Remarks</span></span>

<span data-ttu-id="a3de1-121">您可以建立可供格式化檔案的所有視圖使用的通用控制項，而且可以建立可供特定視圖使用的 view 控制項。</span><span class="sxs-lookup"><span data-stu-id="a3de1-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="a3de1-122">下列元素會指定這些自訂控制項的名稱：</span><span class="sxs-lookup"><span data-stu-id="a3de1-122">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="a3de1-123">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a3de1-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="a3de1-124">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a3de1-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="a3de1-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3de1-125">See Also</span></span>

[<span data-ttu-id="a3de1-126">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a3de1-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="a3de1-127">設定之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a3de1-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="a3de1-128">檢視之控制項的控制項的名稱元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="a3de1-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="a3de1-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="a3de1-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
