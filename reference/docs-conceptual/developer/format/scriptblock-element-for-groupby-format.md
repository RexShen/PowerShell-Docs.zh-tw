---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 的 ScriptBlock 元素 (格式)
description: GroupBy 的 ScriptBlock 元素 (格式)
ms.openlocfilehash: 117cbef93889046626741449886a1caaa39815cb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665240"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="eb62a-103">GroupBy 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="eb62a-103">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="eb62a-104">指定每當新群組值變更時，會啟動新群組的腳本。</span><span class="sxs-lookup"><span data-stu-id="eb62a-104">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="eb62a-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) groupby 專案的 (格式)  (格式的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="eb62a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="eb62a-106">語法</span><span class="sxs-lookup"><span data-stu-id="eb62a-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="eb62a-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="eb62a-107">Attributes and Elements</span></span>

<span data-ttu-id="eb62a-108">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="eb62a-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="eb62a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="eb62a-109">Attributes</span></span>

<span data-ttu-id="eb62a-110">無。</span><span class="sxs-lookup"><span data-stu-id="eb62a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="eb62a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="eb62a-111">Child Elements</span></span>

<span data-ttu-id="eb62a-112">無。</span><span class="sxs-lookup"><span data-stu-id="eb62a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="eb62a-113">父項目</span><span class="sxs-lookup"><span data-stu-id="eb62a-113">Parent Elements</span></span>

|<span data-ttu-id="eb62a-114">元素</span><span class="sxs-lookup"><span data-stu-id="eb62a-114">Element</span></span>|<span data-ttu-id="eb62a-115">描述</span><span class="sxs-lookup"><span data-stu-id="eb62a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eb62a-116">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="eb62a-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="eb62a-117">定義如何顯示 .NET 物件的群組。</span><span class="sxs-lookup"><span data-stu-id="eb62a-117">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="eb62a-118">文字值</span><span class="sxs-lookup"><span data-stu-id="eb62a-118">Text Value</span></span>

<span data-ttu-id="eb62a-119">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="eb62a-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="eb62a-120">備註</span><span class="sxs-lookup"><span data-stu-id="eb62a-120">Remarks</span></span>

<span data-ttu-id="eb62a-121">每當此腳本的值變更時，PowerShell 就會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="eb62a-121">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="eb62a-122">當指定這個專案時，您無法指定 [PropertyName](propertyname-element-for-groupby-format.md) 元素來啟動新群組。</span><span class="sxs-lookup"><span data-stu-id="eb62a-122">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb62a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb62a-123">See Also</span></span>

[<span data-ttu-id="eb62a-124">GroupBy 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="eb62a-124">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="eb62a-125">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="eb62a-125">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="eb62a-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="eb62a-126">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
