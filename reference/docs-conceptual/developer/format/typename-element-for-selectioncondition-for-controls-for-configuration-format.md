---
title: 設定之控制項的 SelectionCondition 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 477c8711-fffc-4f92-af45-6d4f80990474
caps.latest.revision: 7
ms.openlocfilehash: 60f02f3240c5574e1b1f9027b060bd9af89a11d2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361607"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="ab2f1-102">設定之控制項的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ab2f1-102">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="ab2f1-103">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="ab2f1-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="ab2f1-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="ab2f1-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="ab2f1-105">Configuration 元素（格式）控制項的設定（格式）控制項元素的元素，用於控制項的設定（format） CustomControl 元素，用於控制項的 CustomControl 的設定（格式） CustomEntries 元素設定（格式） CustomEntry 元素，用於 CustomControl 的設定（格式）之 entryselectedby 元素（適用于 SelectionCondition for 之 entryselectedby 的設定（Format） CustomEntry 元素）之控制項的 CustomEntry設定之控制項的 SelectionCondition 設定（格式） TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ab2f1-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ab2f1-106">語法</span><span class="sxs-lookup"><span data-stu-id="ab2f1-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="ab2f1-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="ab2f1-107">Attributes and Elements</span></span>

<span data-ttu-id="ab2f1-108">下列各節說明屬性、子專案，以及 `TypeName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="ab2f1-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ab2f1-109">屬性</span><span class="sxs-lookup"><span data-stu-id="ab2f1-109">Attributes</span></span>

<span data-ttu-id="ab2f1-110">無。</span><span class="sxs-lookup"><span data-stu-id="ab2f1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ab2f1-111">子元素</span><span class="sxs-lookup"><span data-stu-id="ab2f1-111">Child Elements</span></span>

<span data-ttu-id="ab2f1-112">無。</span><span class="sxs-lookup"><span data-stu-id="ab2f1-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ab2f1-113">父元素</span><span class="sxs-lookup"><span data-stu-id="ab2f1-113">Parent Elements</span></span>

|<span data-ttu-id="ab2f1-114">元素</span><span class="sxs-lookup"><span data-stu-id="ab2f1-114">Element</span></span>|<span data-ttu-id="ab2f1-115">描述</span><span class="sxs-lookup"><span data-stu-id="ab2f1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab2f1-116">適用于 CustomEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ab2f1-116">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="ab2f1-117">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="ab2f1-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ab2f1-118">文字值</span><span class="sxs-lookup"><span data-stu-id="ab2f1-118">Text Value</span></span>

<span data-ttu-id="ab2f1-119">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="ab2f1-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="ab2f1-120">備註</span><span class="sxs-lookup"><span data-stu-id="ab2f1-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="ab2f1-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab2f1-121">See Also</span></span>

[<span data-ttu-id="ab2f1-122">適用于 CustomEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ab2f1-122">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="ab2f1-123">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="ab2f1-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
