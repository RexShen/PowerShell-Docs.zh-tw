---
title: WideControl (格式的 AutoSize 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 64e62142738916978b37eb1cd3a73536b0447099
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783869"
---
# <a name="autosize-element-for-widecontrol-format"></a><span data-ttu-id="d7530-102">WideControl 的 AutoSize 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d7530-102">AutoSize Element for WideControl (Format)</span></span>

<span data-ttu-id="d7530-103">指定是否根據資料大小來調整資料行大小和資料行數目。</span><span class="sxs-lookup"><span data-stu-id="d7530-103">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>

<span data-ttu-id="d7530-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) WideControl 元素 (format) Autosize 元素 for WideControl (Format) </span><span class="sxs-lookup"><span data-stu-id="d7530-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) Autosize Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d7530-105">語法</span><span class="sxs-lookup"><span data-stu-id="d7530-105">Syntax</span></span>

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d7530-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d7530-106">Attributes and Elements</span></span>

<span data-ttu-id="d7530-107">下列各節說明屬性、子專案和元素的父元素 `AutoSize` 。</span><span class="sxs-lookup"><span data-stu-id="d7530-107">The following sections describe attributes, child elements, and the parent element of the `AutoSize` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d7530-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d7530-108">Attributes</span></span>

<span data-ttu-id="d7530-109">無。</span><span class="sxs-lookup"><span data-stu-id="d7530-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d7530-110">子元素</span><span class="sxs-lookup"><span data-stu-id="d7530-110">Child Elements</span></span>

<span data-ttu-id="d7530-111">無</span><span class="sxs-lookup"><span data-stu-id="d7530-111">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d7530-112">父項目</span><span class="sxs-lookup"><span data-stu-id="d7530-112">Parent Elements</span></span>

|<span data-ttu-id="d7530-113">元素</span><span class="sxs-lookup"><span data-stu-id="d7530-113">Element</span></span>|<span data-ttu-id="d7530-114">描述</span><span class="sxs-lookup"><span data-stu-id="d7530-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d7530-115">WideControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d7530-115">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="d7530-116">定義視圖的寬 (單一值) 清單格式。</span><span class="sxs-lookup"><span data-stu-id="d7530-116">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d7530-117">備註</span><span class="sxs-lookup"><span data-stu-id="d7530-117">Remarks</span></span>

<span data-ttu-id="d7530-118">定義寬視圖時，您可以加入 `AutoSize` 元素或[ColumnNumber](./columnnumber-element-for-widecontrol-format.md)專案，但無法同時新增這兩個專案。</span><span class="sxs-lookup"><span data-stu-id="d7530-118">When defining a wide view, you can add the `AutoSize` element or the [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element, but you cannot add both.</span></span>

<span data-ttu-id="d7530-119">如需有關寬視圖元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d7530-119">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="d7530-120">如需寬視圖的範例，請參閱[寬視圖 (基本) ](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="d7530-120">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d7530-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7530-121">See Also</span></span>

[<span data-ttu-id="d7530-122">WideControl 的 ColumnNumber 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d7530-122">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="d7530-123">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="d7530-123">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d7530-124">WideControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d7530-124">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="d7530-125">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="d7530-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
