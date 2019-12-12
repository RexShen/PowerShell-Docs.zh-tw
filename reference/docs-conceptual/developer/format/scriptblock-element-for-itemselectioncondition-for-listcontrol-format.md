---
title: ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362097"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="475d0-102">ListControl 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="475d0-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="475d0-103">指定觸發條件的腳本。</span><span class="sxs-lookup"><span data-stu-id="475d0-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="475d0-104">當此腳本評估為 `true`時，會符合條件，而且會使用清單專案。</span><span class="sxs-lookup"><span data-stu-id="475d0-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="475d0-105">定義清單視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="475d0-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="475d0-106">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（format） ListEntries 元素（適用于 ListEntry 的 ListEntries for ListControl （Format） ListItems 元素） ListControl （Format） ListEntry 元素適用于 ListItems 的 ListControl （Format） [清單控制項（格式）] 元素，用於 ItemSelectionCondition for ListControl 的 ListControl （Format） ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="475d0-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="475d0-107">語法</span><span class="sxs-lookup"><span data-stu-id="475d0-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="475d0-108">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="475d0-108">Attributes and Elements</span></span>

<span data-ttu-id="475d0-109">下列各節說明屬性、子專案，以及 `ScriptBlock` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="475d0-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="475d0-110">屬性</span><span class="sxs-lookup"><span data-stu-id="475d0-110">Attributes</span></span>

<span data-ttu-id="475d0-111">無。</span><span class="sxs-lookup"><span data-stu-id="475d0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="475d0-112">子元素</span><span class="sxs-lookup"><span data-stu-id="475d0-112">Child Elements</span></span>

<span data-ttu-id="475d0-113">無。</span><span class="sxs-lookup"><span data-stu-id="475d0-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="475d0-114">父元素</span><span class="sxs-lookup"><span data-stu-id="475d0-114">Parent Elements</span></span>

|<span data-ttu-id="475d0-115">元素</span><span class="sxs-lookup"><span data-stu-id="475d0-115">Element</span></span>|<span data-ttu-id="475d0-116">描述</span><span class="sxs-lookup"><span data-stu-id="475d0-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="475d0-117">ListControl 之專案的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="475d0-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="475d0-118">定義必須存在才能使用此清單專案的條件。</span><span class="sxs-lookup"><span data-stu-id="475d0-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="475d0-119">文字值</span><span class="sxs-lookup"><span data-stu-id="475d0-119">Text Value</span></span>

<span data-ttu-id="475d0-120">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="475d0-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="475d0-121">備註</span><span class="sxs-lookup"><span data-stu-id="475d0-121">Remarks</span></span>

<span data-ttu-id="475d0-122">如果使用這個元素，則在定義選取條件時，不能指定 `PropertyName` 元素。</span><span class="sxs-lookup"><span data-stu-id="475d0-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="475d0-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="475d0-123">See Also</span></span>

[<span data-ttu-id="475d0-124">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="475d0-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
