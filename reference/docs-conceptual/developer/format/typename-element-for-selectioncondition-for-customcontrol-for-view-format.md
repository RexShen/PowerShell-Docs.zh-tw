---
title: CustomControl for View 的 SelectionCondition 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c65171-4d4c-46a9-a545-591df058acd1
caps.latest.revision: 7
ms.openlocfilehash: 00e9ae0916dd6d22602b99b201c9c4b7e549dc48
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361587"
---
# <a name="typename-element-for-selectioncondition-for-customcontrol-for-view--format"></a><span data-ttu-id="2b285-102">檢視之 CustomControl 的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2b285-102">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>

<span data-ttu-id="2b285-103">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="2b285-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="2b285-104">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="2b285-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="2b285-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素 for view （format） CustomEntries 元素 for CustomEntry for view （format） CustomEntries 元素Format） CustomItem 元素，用於 CustomControl for view （format） SelectionCondition 元素之 entryselectedby for CustomControl for view （format） TypeName 元素 SelectionCondition for view （格式）</span><span class="sxs-lookup"><span data-stu-id="2b285-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2b285-106">語法</span><span class="sxs-lookup"><span data-stu-id="2b285-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="2b285-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="2b285-107">Attributes and Elements</span></span>

<span data-ttu-id="2b285-108">下列各節說明屬性、子專案，以及 `TypeName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="2b285-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2b285-109">屬性</span><span class="sxs-lookup"><span data-stu-id="2b285-109">Attributes</span></span>

<span data-ttu-id="2b285-110">無。</span><span class="sxs-lookup"><span data-stu-id="2b285-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2b285-111">子元素</span><span class="sxs-lookup"><span data-stu-id="2b285-111">Child Elements</span></span>

<span data-ttu-id="2b285-112">無。</span><span class="sxs-lookup"><span data-stu-id="2b285-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2b285-113">父元素</span><span class="sxs-lookup"><span data-stu-id="2b285-113">Parent Elements</span></span>

|<span data-ttu-id="2b285-114">元素</span><span class="sxs-lookup"><span data-stu-id="2b285-114">Element</span></span>|<span data-ttu-id="2b285-115">描述</span><span class="sxs-lookup"><span data-stu-id="2b285-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2b285-116">CustomControl for View 的之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2b285-116">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="2b285-117">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="2b285-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2b285-118">文字值</span><span class="sxs-lookup"><span data-stu-id="2b285-118">Text Value</span></span>

<span data-ttu-id="2b285-119">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="2b285-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="2b285-120">備註</span><span class="sxs-lookup"><span data-stu-id="2b285-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="2b285-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b285-121">See Also</span></span>

[<span data-ttu-id="2b285-122">CustomControl for View 的之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2b285-122">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="2b285-123">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="2b285-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
