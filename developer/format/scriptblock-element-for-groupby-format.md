---
title: GroupBy （格式） 的指令碼區塊項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229312"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="1ce69-102">GroupBy 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1ce69-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="1ce69-103">指定的指令碼，其值變更時，會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="1ce69-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="1ce69-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） 的 GroupBy （格式） 的指令碼區塊項目</span><span class="sxs-lookup"><span data-stu-id="1ce69-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1ce69-105">語法</span><span class="sxs-lookup"><span data-stu-id="1ce69-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1ce69-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="1ce69-106">Attributes and Elements</span></span>

<span data-ttu-id="1ce69-107">下列各節說明屬性、 子項目和父項目`ScriptBlock`項目。</span><span class="sxs-lookup"><span data-stu-id="1ce69-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1ce69-108">屬性</span><span class="sxs-lookup"><span data-stu-id="1ce69-108">Attributes</span></span>

<span data-ttu-id="1ce69-109">無。</span><span class="sxs-lookup"><span data-stu-id="1ce69-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1ce69-110">子元素</span><span class="sxs-lookup"><span data-stu-id="1ce69-110">Child Elements</span></span>

<span data-ttu-id="1ce69-111">無。</span><span class="sxs-lookup"><span data-stu-id="1ce69-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1ce69-112">父項目</span><span class="sxs-lookup"><span data-stu-id="1ce69-112">Parent Elements</span></span>

|<span data-ttu-id="1ce69-113">項目</span><span class="sxs-lookup"><span data-stu-id="1ce69-113">Element</span></span>|<span data-ttu-id="1ce69-114">描述</span><span class="sxs-lookup"><span data-stu-id="1ce69-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1ce69-115">檢視 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="1ce69-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="1ce69-116">定義一組.NET 物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="1ce69-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1ce69-117">文字值</span><span class="sxs-lookup"><span data-stu-id="1ce69-117">Text Value</span></span>

<span data-ttu-id="1ce69-118">指定評估指令碼。</span><span class="sxs-lookup"><span data-stu-id="1ce69-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ce69-119">備註</span><span class="sxs-lookup"><span data-stu-id="1ce69-119">Remarks</span></span>

<span data-ttu-id="1ce69-120">此指令碼的值變更時，PowerShell 會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="1ce69-120">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="1ce69-121">當指定這個項目時，您無法指定[PropertyName](propertyname-element-for-groupby-format.md)啟動新的群組項目。</span><span class="sxs-lookup"><span data-stu-id="1ce69-121">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ce69-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ce69-122">See Also</span></span>

[<span data-ttu-id="1ce69-123">GroupBy （格式） 的屬性名稱項目</span><span class="sxs-lookup"><span data-stu-id="1ce69-123">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="1ce69-124">檢視 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="1ce69-124">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="1ce69-125">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="1ce69-125">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
