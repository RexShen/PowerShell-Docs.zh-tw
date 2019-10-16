---
title: TableControl 之之 entryselectedby 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361627"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="24920-102">TableControl 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="24920-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="24920-103">指定使用此資料表視圖專案的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="24920-103">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="24920-104">可以針對資料表專案指定的類型數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="24920-104">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="24920-105">之 entryselectedby 的設定元素（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（格式）之 entryselectedby 元素（格式） TypeName 元素針對 TableRowEntry （格式）</span><span class="sxs-lookup"><span data-stu-id="24920-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="24920-106">語法</span><span class="sxs-lookup"><span data-stu-id="24920-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="24920-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="24920-107">Attributes and Elements</span></span>

<span data-ttu-id="24920-108">下列各節說明屬性、子專案，以及 `TypeName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="24920-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="24920-109">屬性</span><span class="sxs-lookup"><span data-stu-id="24920-109">Attributes</span></span>

<span data-ttu-id="24920-110">無。</span><span class="sxs-lookup"><span data-stu-id="24920-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="24920-111">子元素</span><span class="sxs-lookup"><span data-stu-id="24920-111">Child Elements</span></span>

<span data-ttu-id="24920-112">無。</span><span class="sxs-lookup"><span data-stu-id="24920-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="24920-113">父元素</span><span class="sxs-lookup"><span data-stu-id="24920-113">Parent Elements</span></span>

|<span data-ttu-id="24920-114">元素</span><span class="sxs-lookup"><span data-stu-id="24920-114">Element</span></span>|<span data-ttu-id="24920-115">描述</span><span class="sxs-lookup"><span data-stu-id="24920-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="24920-116">之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="24920-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="24920-117">定義使用此專案的 .NET 類型，或必須存在才能使用此專案的條件。</span><span class="sxs-lookup"><span data-stu-id="24920-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="24920-118">文字值</span><span class="sxs-lookup"><span data-stu-id="24920-118">Text Value</span></span>

<span data-ttu-id="24920-119">指定 .NET 類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="24920-119">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="24920-120">備註</span><span class="sxs-lookup"><span data-stu-id="24920-120">Remarks</span></span>

<span data-ttu-id="24920-121">每個清單專案都必須定義至少一個型別名稱、選擇集或選取條件。</span><span class="sxs-lookup"><span data-stu-id="24920-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="24920-122">如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="24920-122">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="24920-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24920-123">See Also</span></span>

[<span data-ttu-id="24920-124">建立資料表視圖</span><span class="sxs-lookup"><span data-stu-id="24920-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="24920-125">之 entryselectedby 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="24920-125">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="24920-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="24920-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
