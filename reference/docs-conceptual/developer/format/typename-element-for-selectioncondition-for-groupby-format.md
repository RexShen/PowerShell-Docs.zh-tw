---
title: GroupBy (格式的 SelectionCondition 的 TypeName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ea1e0cb50c3a749f6c26d13fff4b001240ce6b95
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772547"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="cebef-102">GroupBy 之 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="cebef-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="cebef-103">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="cebef-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="cebef-104">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="cebef-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="cebef-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) GroupBy 元素用於 CustomEntries 的專案 (格式的 CustomControl 的 CustomControl 專案) format (格式) CustomEntry 元素的 CustomControl 的 groupby (格式)  (之 entryselectedby 元素 CustomEntry 的 groupby) 格式的 SelectionCondition 專案 (的之 entryselectedby 專案</span><span class="sxs-lookup"><span data-stu-id="cebef-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cebef-106">語法</span><span class="sxs-lookup"><span data-stu-id="cebef-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="cebef-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cebef-107">Attributes and Elements</span></span>

<span data-ttu-id="cebef-108">下列各節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="cebef-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cebef-109">屬性</span><span class="sxs-lookup"><span data-stu-id="cebef-109">Attributes</span></span>

<span data-ttu-id="cebef-110">無。</span><span class="sxs-lookup"><span data-stu-id="cebef-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cebef-111">子元素</span><span class="sxs-lookup"><span data-stu-id="cebef-111">Child Elements</span></span>

<span data-ttu-id="cebef-112">無。</span><span class="sxs-lookup"><span data-stu-id="cebef-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cebef-113">父項目</span><span class="sxs-lookup"><span data-stu-id="cebef-113">Parent Elements</span></span>

|<span data-ttu-id="cebef-114">元素</span><span class="sxs-lookup"><span data-stu-id="cebef-114">Element</span></span>|<span data-ttu-id="cebef-115">描述</span><span class="sxs-lookup"><span data-stu-id="cebef-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cebef-116">GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="cebef-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="cebef-117">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="cebef-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cebef-118">文字值</span><span class="sxs-lookup"><span data-stu-id="cebef-118">Text Value</span></span>

<span data-ttu-id="cebef-119">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。</span><span class="sxs-lookup"><span data-stu-id="cebef-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="cebef-120">備註</span><span class="sxs-lookup"><span data-stu-id="cebef-120">Remarks</span></span>

<span data-ttu-id="cebef-121">當指定此元素時，您無法指定 `SelectionSetName` 元素。</span><span class="sxs-lookup"><span data-stu-id="cebef-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="cebef-122">如需定義選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="cebef-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cebef-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cebef-123">See Also</span></span>

[<span data-ttu-id="cebef-124">GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="cebef-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="cebef-125">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="cebef-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
