---
title: TableControl （格式） 的 EntrySelectedBy TypeName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083955"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="fa7a2-102">TableControl 之 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fa7a2-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="fa7a2-103">指定.NET 型別，使用 [資料表] 檢視的這個項目。</span><span class="sxs-lookup"><span data-stu-id="fa7a2-103">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="fa7a2-104">可供指定的資料表項目類型的數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="fa7a2-104">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="fa7a2-105">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 （格式） TableRowEntry 項目 （格式） EntrySelectedBy 項目 （格式） 類型名稱項目 EntrySelectedBy針對 TableRowEntry （格式）</span><span class="sxs-lookup"><span data-stu-id="fa7a2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fa7a2-106">語法</span><span class="sxs-lookup"><span data-stu-id="fa7a2-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fa7a2-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fa7a2-107">Attributes and Elements</span></span>

<span data-ttu-id="fa7a2-108">下列各節說明屬性、 子項目和父項目`TypeName`項目。</span><span class="sxs-lookup"><span data-stu-id="fa7a2-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fa7a2-109">屬性</span><span class="sxs-lookup"><span data-stu-id="fa7a2-109">Attributes</span></span>

<span data-ttu-id="fa7a2-110">無。</span><span class="sxs-lookup"><span data-stu-id="fa7a2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fa7a2-111">子元素</span><span class="sxs-lookup"><span data-stu-id="fa7a2-111">Child Elements</span></span>

<span data-ttu-id="fa7a2-112">無。</span><span class="sxs-lookup"><span data-stu-id="fa7a2-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fa7a2-113">父項目</span><span class="sxs-lookup"><span data-stu-id="fa7a2-113">Parent Elements</span></span>

|<span data-ttu-id="fa7a2-114">項目</span><span class="sxs-lookup"><span data-stu-id="fa7a2-114">Element</span></span>|<span data-ttu-id="fa7a2-115">描述</span><span class="sxs-lookup"><span data-stu-id="fa7a2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fa7a2-116">EntrySelectedBy 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="fa7a2-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="fa7a2-117">定義.NET 型別，使用此項目或要使用此項目必須存在的條件。</span><span class="sxs-lookup"><span data-stu-id="fa7a2-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fa7a2-118">文字值</span><span class="sxs-lookup"><span data-stu-id="fa7a2-118">Text Value</span></span>

<span data-ttu-id="fa7a2-119">指定.NET 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="fa7a2-119">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="fa7a2-120">備註</span><span class="sxs-lookup"><span data-stu-id="fa7a2-120">Remarks</span></span>

<span data-ttu-id="fa7a2-121">每個清單項目必須至少一個型別名稱、 選取項目集或選擇條件的定義。</span><span class="sxs-lookup"><span data-stu-id="fa7a2-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="fa7a2-122">資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="fa7a2-122">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fa7a2-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa7a2-123">See Also</span></span>

[<span data-ttu-id="fa7a2-124">建立資料表檢視</span><span class="sxs-lookup"><span data-stu-id="fa7a2-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="fa7a2-125">EntrySelectedBy 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="fa7a2-125">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="fa7a2-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="fa7a2-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
