---
title: View 的 Controls 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bd82666-447f-40fe-bd87-c8b182522f4f
caps.latest.revision: 14
ms.openlocfilehash: 477b8b54c8edd2fa0e6939041d04322d861197c9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363387"
---
# <a name="controls-element-for-view-format"></a><span data-ttu-id="4ea6e-102">檢視的控制項元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4ea6e-102">Controls Element for View (Format)</span></span>

<span data-ttu-id="4ea6e-103">定義可供特定視圖使用的 view 控制項。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-103">Defines the view controls that can be used by a specific view.</span></span>

<span data-ttu-id="4ea6e-104">設定專案（格式） ViewDefinitions 元素（格式） View 元素（格式） Controls 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4ea6e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4ea6e-105">語法</span><span class="sxs-lookup"><span data-stu-id="4ea6e-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4ea6e-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="4ea6e-106">Attributes and Elements</span></span>

<span data-ttu-id="4ea6e-107">下列各節說明 `Controls` 元素的屬性、子專案和父元素。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-107">The following sections describe the attributes, child elements, and parent elements of the `Controls` element.</span></span> <span data-ttu-id="4ea6e-108">此元素必須至少有一個子專案。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-108">This element must have at least one child element.</span></span> <span data-ttu-id="4ea6e-109">子項目沒有最大數目，也沒有順序重要性。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-109">There is no maximum number of child elements, nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="4ea6e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="4ea6e-110">Attributes</span></span>

<span data-ttu-id="4ea6e-111">無。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4ea6e-112">子元素</span><span class="sxs-lookup"><span data-stu-id="4ea6e-112">Child Elements</span></span>

|<span data-ttu-id="4ea6e-113">元素</span><span class="sxs-lookup"><span data-stu-id="4ea6e-113">Element</span></span>|<span data-ttu-id="4ea6e-114">描述</span><span class="sxs-lookup"><span data-stu-id="4ea6e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4ea6e-115">View 控制項的控制項元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4ea6e-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="4ea6e-116">定義可供視圖使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-116">Defines a control that can be used by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4ea6e-117">父元素</span><span class="sxs-lookup"><span data-stu-id="4ea6e-117">Parent Elements</span></span>

|<span data-ttu-id="4ea6e-118">元素</span><span class="sxs-lookup"><span data-stu-id="4ea6e-118">Element</span></span>|<span data-ttu-id="4ea6e-119">描述</span><span class="sxs-lookup"><span data-stu-id="4ea6e-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4ea6e-120">View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4ea6e-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="4ea6e-121">定義用來顯示一或多個 .NET 物件成員的視圖。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-121">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4ea6e-122">備註</span><span class="sxs-lookup"><span data-stu-id="4ea6e-122">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="4ea6e-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ea6e-123">See Also</span></span>

[<span data-ttu-id="4ea6e-124">Control 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4ea6e-124">Control Element (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="4ea6e-125">View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4ea6e-125">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="4ea6e-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="4ea6e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
