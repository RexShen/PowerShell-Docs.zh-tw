---
title: View 之控制項的 SelectionCondition 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7141aefc-6656-4c52-8a9c-c2bfc9c87be9
caps.latest.revision: 6
ms.openlocfilehash: 7a697c286ec9efe750930739cdfa2580003365dd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361597"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="bd747-102">檢視之控制項的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="bd747-102">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="bd747-103">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="bd747-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="bd747-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="bd747-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="bd747-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素CustomControl for view （format） CustomEntry 元素的 CustomEntries for view （format）之 entryselectedby 元素 for CustomEntry for view （format） SelectionCondition 元素 for controls 的控制項（格式）Format）控制項的 SelectionCondition 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="bd747-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) TypeName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bd747-106">語法</span><span class="sxs-lookup"><span data-stu-id="bd747-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="bd747-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="bd747-107">Attributes and Elements</span></span>

<span data-ttu-id="bd747-108">下列各節說明屬性、子專案，以及 `TypeName` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="bd747-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bd747-109">屬性</span><span class="sxs-lookup"><span data-stu-id="bd747-109">Attributes</span></span>

<span data-ttu-id="bd747-110">無。</span><span class="sxs-lookup"><span data-stu-id="bd747-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bd747-111">子元素</span><span class="sxs-lookup"><span data-stu-id="bd747-111">Child Elements</span></span>

<span data-ttu-id="bd747-112">無。</span><span class="sxs-lookup"><span data-stu-id="bd747-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bd747-113">父元素</span><span class="sxs-lookup"><span data-stu-id="bd747-113">Parent Elements</span></span>

|<span data-ttu-id="bd747-114">元素</span><span class="sxs-lookup"><span data-stu-id="bd747-114">Element</span></span>|<span data-ttu-id="bd747-115">描述</span><span class="sxs-lookup"><span data-stu-id="bd747-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bd747-116">View 之控制項的之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="bd747-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="bd747-117">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="bd747-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bd747-118">文字值</span><span class="sxs-lookup"><span data-stu-id="bd747-118">Text Value</span></span>

<span data-ttu-id="bd747-119">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="bd747-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="bd747-120">備註</span><span class="sxs-lookup"><span data-stu-id="bd747-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="bd747-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd747-121">See Also</span></span>

[<span data-ttu-id="bd747-122">View 之控制項的之 entryselectedby 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="bd747-122">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="bd747-123">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="bd747-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
