---
ms.date: 09/13/2016
ms.topic: reference
title: DisplayError 元素 (格式)
description: DisplayError 元素 (格式)
ms.openlocfilehash: fb54df86a3558263687a8c417870495b7066f563
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649929"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="ad0b5-103">DisplayError 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ad0b5-103">DisplayError Element (Format)</span></span>

<span data-ttu-id="ad0b5-104">指定在顯示資料的錯誤發生時，顯示 #ERR 的字串。</span><span class="sxs-lookup"><span data-stu-id="ad0b5-104">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="ad0b5-105">Configuration 元素 (格式) DefaultSettings 元素 (格式) DisplayError 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="ad0b5-105">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ad0b5-106">語法</span><span class="sxs-lookup"><span data-stu-id="ad0b5-106">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ad0b5-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ad0b5-107">Attributes and Elements</span></span>

<span data-ttu-id="ad0b5-108">下列各節說明屬性、子專案和元素的父元素 `DisplayError` 。</span><span class="sxs-lookup"><span data-stu-id="ad0b5-108">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ad0b5-109">屬性</span><span class="sxs-lookup"><span data-stu-id="ad0b5-109">Attributes</span></span>

<span data-ttu-id="ad0b5-110">無。</span><span class="sxs-lookup"><span data-stu-id="ad0b5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ad0b5-111">子元素</span><span class="sxs-lookup"><span data-stu-id="ad0b5-111">Child Elements</span></span>

<span data-ttu-id="ad0b5-112">無。</span><span class="sxs-lookup"><span data-stu-id="ad0b5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ad0b5-113">父項目</span><span class="sxs-lookup"><span data-stu-id="ad0b5-113">Parent Elements</span></span>

|<span data-ttu-id="ad0b5-114">元素</span><span class="sxs-lookup"><span data-stu-id="ad0b5-114">Element</span></span>|<span data-ttu-id="ad0b5-115">描述</span><span class="sxs-lookup"><span data-stu-id="ad0b5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ad0b5-116">DefaultSettings 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ad0b5-116">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="ad0b5-117">定義適用于格式檔案所有視圖的一般設定。</span><span class="sxs-lookup"><span data-stu-id="ad0b5-117">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ad0b5-118">備註</span><span class="sxs-lookup"><span data-stu-id="ad0b5-118">Remarks</span></span>

<span data-ttu-id="ad0b5-119">根據預設，當嘗試顯示資料時，如果發生錯誤，資料的位置會保留空白。</span><span class="sxs-lookup"><span data-stu-id="ad0b5-119">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="ad0b5-120">當這個元素設定為 true 時，將會顯示 #ERR 字串。</span><span class="sxs-lookup"><span data-stu-id="ad0b5-120">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad0b5-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad0b5-121">See Also</span></span>

[<span data-ttu-id="ad0b5-122">DefaultSettings 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ad0b5-122">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="ad0b5-123">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="ad0b5-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
