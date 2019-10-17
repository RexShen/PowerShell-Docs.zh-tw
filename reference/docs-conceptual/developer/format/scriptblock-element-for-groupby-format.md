---
title: GroupBy 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364927"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="e9a27-102">GroupBy 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e9a27-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="e9a27-103">指定每當新群組的值變更時，就會啟動的腳本。</span><span class="sxs-lookup"><span data-stu-id="e9a27-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="e9a27-104">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（格式）-GroupBy 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e9a27-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e9a27-105">語法</span><span class="sxs-lookup"><span data-stu-id="e9a27-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e9a27-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="e9a27-106">Attributes and Elements</span></span>

<span data-ttu-id="e9a27-107">下列各節說明屬性、子專案，以及 `ScriptBlock` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="e9a27-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e9a27-108">屬性</span><span class="sxs-lookup"><span data-stu-id="e9a27-108">Attributes</span></span>

<span data-ttu-id="e9a27-109">無。</span><span class="sxs-lookup"><span data-stu-id="e9a27-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e9a27-110">子元素</span><span class="sxs-lookup"><span data-stu-id="e9a27-110">Child Elements</span></span>

<span data-ttu-id="e9a27-111">無。</span><span class="sxs-lookup"><span data-stu-id="e9a27-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e9a27-112">父元素</span><span class="sxs-lookup"><span data-stu-id="e9a27-112">Parent Elements</span></span>

|<span data-ttu-id="e9a27-113">元素</span><span class="sxs-lookup"><span data-stu-id="e9a27-113">Element</span></span>|<span data-ttu-id="e9a27-114">描述</span><span class="sxs-lookup"><span data-stu-id="e9a27-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e9a27-115">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e9a27-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="e9a27-116">定義一組 .NET 物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="e9a27-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e9a27-117">文字值</span><span class="sxs-lookup"><span data-stu-id="e9a27-117">Text Value</span></span>

<span data-ttu-id="e9a27-118">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="e9a27-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="e9a27-119">備註</span><span class="sxs-lookup"><span data-stu-id="e9a27-119">Remarks</span></span>

<span data-ttu-id="e9a27-120">每當此腳本的值變更時，PowerShell 就會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="e9a27-120">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="e9a27-121">當指定此元素時，您無法指定[PropertyName](propertyname-element-for-groupby-format.md)元素來啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="e9a27-121">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9a27-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9a27-122">See Also</span></span>

[<span data-ttu-id="e9a27-123">GroupBy 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e9a27-123">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="e9a27-124">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e9a27-124">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="e9a27-125">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="e9a27-125">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)