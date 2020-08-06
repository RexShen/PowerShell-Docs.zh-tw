---
title: 設定 (格式) 之控制項的 SelectionCondition 的 TypeName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2db856d1b84dded315204d8c8574ae86acb63515
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780061"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="b7942-102">設定之控制項的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b7942-102">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="b7942-103">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="b7942-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="b7942-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="b7942-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="b7942-105">Configuration 元素 (格式) Controls 設定的控制項元素 (格式設定的控制項) 控制項專案 (格式) 設定 (格式的控制項的 CustomControl 的 CustomEntries 元素) CustomEntry 元素針對設定 (格式的控制項的 CustomControl) 之 entryselectedby 元素，用於 CustomEntry 的之 entryselectedby for CustomEntry for configuration (Format) TypeName 元素 For SelectionCondition for configuration (格式) )  (</span><span class="sxs-lookup"><span data-stu-id="b7942-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b7942-106">語法</span><span class="sxs-lookup"><span data-stu-id="b7942-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="b7942-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b7942-107">Attributes and Elements</span></span>

<span data-ttu-id="b7942-108">下列各節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="b7942-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b7942-109">屬性</span><span class="sxs-lookup"><span data-stu-id="b7942-109">Attributes</span></span>

<span data-ttu-id="b7942-110">無。</span><span class="sxs-lookup"><span data-stu-id="b7942-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b7942-111">子元素</span><span class="sxs-lookup"><span data-stu-id="b7942-111">Child Elements</span></span>

<span data-ttu-id="b7942-112">無。</span><span class="sxs-lookup"><span data-stu-id="b7942-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b7942-113">父項目</span><span class="sxs-lookup"><span data-stu-id="b7942-113">Parent Elements</span></span>

|<span data-ttu-id="b7942-114">元素</span><span class="sxs-lookup"><span data-stu-id="b7942-114">Element</span></span>|<span data-ttu-id="b7942-115">描述</span><span class="sxs-lookup"><span data-stu-id="b7942-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7942-116">適用于 CustomEntry 之之 entryselectedby 的 SelectionCondition 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="b7942-116">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="b7942-117">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="b7942-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b7942-118">文字值</span><span class="sxs-lookup"><span data-stu-id="b7942-118">Text Value</span></span>

<span data-ttu-id="b7942-119">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。</span><span class="sxs-lookup"><span data-stu-id="b7942-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="b7942-120">備註</span><span class="sxs-lookup"><span data-stu-id="b7942-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="b7942-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7942-121">See Also</span></span>

[<span data-ttu-id="b7942-122">適用于 CustomEntry 之之 entryselectedby 的 SelectionCondition 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="b7942-122">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="b7942-123">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="b7942-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
