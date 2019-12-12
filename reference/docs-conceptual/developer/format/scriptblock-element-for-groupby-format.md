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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364927"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="491fe-102">GroupBy 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="491fe-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="491fe-103">指定每當新群組的值變更時，就會啟動的腳本。</span><span class="sxs-lookup"><span data-stu-id="491fe-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="491fe-104">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（格式）-GroupBy 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="491fe-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="491fe-105">語法</span><span class="sxs-lookup"><span data-stu-id="491fe-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="491fe-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="491fe-106">Attributes and Elements</span></span>

<span data-ttu-id="491fe-107">下列各節說明屬性、子專案，以及 `ScriptBlock` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="491fe-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="491fe-108">屬性</span><span class="sxs-lookup"><span data-stu-id="491fe-108">Attributes</span></span>

<span data-ttu-id="491fe-109">無。</span><span class="sxs-lookup"><span data-stu-id="491fe-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="491fe-110">子元素</span><span class="sxs-lookup"><span data-stu-id="491fe-110">Child Elements</span></span>

<span data-ttu-id="491fe-111">無。</span><span class="sxs-lookup"><span data-stu-id="491fe-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="491fe-112">父元素</span><span class="sxs-lookup"><span data-stu-id="491fe-112">Parent Elements</span></span>

|<span data-ttu-id="491fe-113">元素</span><span class="sxs-lookup"><span data-stu-id="491fe-113">Element</span></span>|<span data-ttu-id="491fe-114">描述</span><span class="sxs-lookup"><span data-stu-id="491fe-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="491fe-115">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="491fe-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="491fe-116">定義一組 .NET 物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="491fe-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="491fe-117">文字值</span><span class="sxs-lookup"><span data-stu-id="491fe-117">Text Value</span></span>

<span data-ttu-id="491fe-118">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="491fe-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="491fe-119">備註</span><span class="sxs-lookup"><span data-stu-id="491fe-119">Remarks</span></span>

<span data-ttu-id="491fe-120">每當此腳本的值變更時，PowerShell 就會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="491fe-120">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="491fe-121">當指定此元素時，您無法指定[PropertyName](propertyname-element-for-groupby-format.md)元素來啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="491fe-121">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="491fe-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="491fe-122">See Also</span></span>

[<span data-ttu-id="491fe-123">GroupBy 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="491fe-123">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="491fe-124">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="491fe-124">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="491fe-125">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="491fe-125">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
