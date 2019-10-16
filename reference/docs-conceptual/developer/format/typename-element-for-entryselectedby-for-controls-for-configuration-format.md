---
title: 設定之控制項的之 entryselectedby 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30bb1382-8c6b-4371-82e6-baf427fa0781
caps.latest.revision: 6
ms.openlocfilehash: cec8c5d76bded321ec1d6a1cd0409d7c88863c03
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368077"
---
# <a name="typename-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="1f7bf-102">設定之控制項的 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1f7bf-102">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="1f7bf-103">指定使用此控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="1f7bf-103">Specifies a .NET type that uses this definition of the control.</span></span> <span data-ttu-id="1f7bf-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="1f7bf-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="1f7bf-105">Configuration 元素（格式）控制設定（format） CustomControl 元素的設定（格式）控制項專案的設定專案（格式） CustomControl 設定的 CustomEntries 元素（格式）Format） CustomEntry 元素，用於 CustomControl 控制項的之 entryselectedby 元素，用於設定（格式）控制項的 CustomEntry for configuration （format） TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="1f7bf-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1f7bf-106">語法</span><span class="sxs-lookup"><span data-stu-id="1f7bf-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="1f7bf-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="1f7bf-107">Attributes and Elements</span></span>

<span data-ttu-id="1f7bf-108">下列各節說明屬性、子專案，以及 `TypeName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="1f7bf-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f7bf-109">屬性</span><span class="sxs-lookup"><span data-stu-id="1f7bf-109">Attributes</span></span>

<span data-ttu-id="1f7bf-110">無。</span><span class="sxs-lookup"><span data-stu-id="1f7bf-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1f7bf-111">子元素</span><span class="sxs-lookup"><span data-stu-id="1f7bf-111">Child Elements</span></span>

<span data-ttu-id="1f7bf-112">無。</span><span class="sxs-lookup"><span data-stu-id="1f7bf-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1f7bf-113">父元素</span><span class="sxs-lookup"><span data-stu-id="1f7bf-113">Parent Elements</span></span>

|<span data-ttu-id="1f7bf-114">元素</span><span class="sxs-lookup"><span data-stu-id="1f7bf-114">Element</span></span>|<span data-ttu-id="1f7bf-115">描述</span><span class="sxs-lookup"><span data-stu-id="1f7bf-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f7bf-116">設定之控制項的 CustomEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1f7bf-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="1f7bf-117">定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="1f7bf-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1f7bf-118">文字值</span><span class="sxs-lookup"><span data-stu-id="1f7bf-118">Text Value</span></span>

<span data-ttu-id="1f7bf-119">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="1f7bf-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="1f7bf-120">備註</span><span class="sxs-lookup"><span data-stu-id="1f7bf-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="1f7bf-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f7bf-121">See Also</span></span>

[<span data-ttu-id="1f7bf-122">設定之控制項的 CustomEntry 的之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1f7bf-122">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="1f7bf-123">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="1f7bf-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
