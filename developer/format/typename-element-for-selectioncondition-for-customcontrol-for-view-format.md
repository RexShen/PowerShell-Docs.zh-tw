---
title: CustomControl 檢視 （格式） 的 SelectionCondition TypeName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c65171-4d4c-46a9-a545-591df058acd1
caps.latest.revision: 7
ms.openlocfilehash: 00e9ae0916dd6d22602b99b201c9c4b7e549dc48
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863204"
---
# <a name="typename-element-for-selectioncondition-for-customcontrol-for-view--format"></a><span data-ttu-id="4b71a-102">檢視之 CustomControl 的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4b71a-102">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>

<span data-ttu-id="4b71a-103">指定觸發條件的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="4b71a-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="4b71a-104">定義自訂控制項的檢視時，會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="4b71a-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="4b71a-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目進行檢視 （格式） 的檢視 （如 CustomControl CustomEntries CustomEntry 元素 CustomControl 的檢視 （格式） CustomEntries 項目格式） 的檢視 （格式） 的檢視 （格式） 類型名稱項目，如 CustomControl 檢視 （格式） 的 SelectionCondition CustomControl EntrySelectedBy SelectionCondition 元素 CustomControl CustomEntry CustomItem 項目</span><span class="sxs-lookup"><span data-stu-id="4b71a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4b71a-106">語法</span><span class="sxs-lookup"><span data-stu-id="4b71a-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="4b71a-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="4b71a-107">Attributes and Elements</span></span>

<span data-ttu-id="4b71a-108">下列各節說明屬性、 子項目和父項目`TypeName`項目。</span><span class="sxs-lookup"><span data-stu-id="4b71a-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4b71a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="4b71a-109">Attributes</span></span>

<span data-ttu-id="4b71a-110">無。</span><span class="sxs-lookup"><span data-stu-id="4b71a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4b71a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4b71a-111">Child Elements</span></span>

<span data-ttu-id="4b71a-112">無。</span><span class="sxs-lookup"><span data-stu-id="4b71a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4b71a-113">父元素</span><span class="sxs-lookup"><span data-stu-id="4b71a-113">Parent Elements</span></span>

|<span data-ttu-id="4b71a-114">元素</span><span class="sxs-lookup"><span data-stu-id="4b71a-114">Element</span></span>|<span data-ttu-id="4b71a-115">描述</span><span class="sxs-lookup"><span data-stu-id="4b71a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4b71a-116">CustomControl 檢視 （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="4b71a-116">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="4b71a-117">定義必須存在，要使用的控制項定義的條件。</span><span class="sxs-lookup"><span data-stu-id="4b71a-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4b71a-118">文字值</span><span class="sxs-lookup"><span data-stu-id="4b71a-118">Text Value</span></span>

<span data-ttu-id="4b71a-119">指定完整的.NET 型別名稱，例如`System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="4b71a-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="4b71a-120">備註</span><span class="sxs-lookup"><span data-stu-id="4b71a-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="4b71a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b71a-121">See Also</span></span>

[<span data-ttu-id="4b71a-122">CustomControl 檢視 （格式） 的 EntrySelectedBy SelectionCondition 項目</span><span class="sxs-lookup"><span data-stu-id="4b71a-122">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="4b71a-123">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="4b71a-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
