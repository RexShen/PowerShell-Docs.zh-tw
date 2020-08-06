---
title: 控制項的 SelectionCondition 的 TypeName 元素，用於 View (Format) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4795c3af40cf60fb8e71185feced18c192b3a0aa
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780044"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="d695d-102">檢視之控制項的 SelectionCondition 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d695d-102">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="d695d-103">指定觸發條件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="d695d-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="d695d-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="d695d-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="d695d-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 CustomControl 格式 (CustomEntries 元素用於 view 的控制項)  ( (格式) 的控制項適用于 CustomEntries 的 CustomEntry 元素，用於 view (Format) 之 entryselectedby 專案 CustomEntry for view (format) SelectionCondition 元素 for view () 格式的控制項的之 entryselectedby (TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="d695d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) TypeName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d695d-106">語法</span><span class="sxs-lookup"><span data-stu-id="d695d-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d695d-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d695d-107">Attributes and Elements</span></span>

<span data-ttu-id="d695d-108">下列各節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="d695d-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d695d-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d695d-109">Attributes</span></span>

<span data-ttu-id="d695d-110">無。</span><span class="sxs-lookup"><span data-stu-id="d695d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d695d-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d695d-111">Child Elements</span></span>

<span data-ttu-id="d695d-112">無。</span><span class="sxs-lookup"><span data-stu-id="d695d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d695d-113">父項目</span><span class="sxs-lookup"><span data-stu-id="d695d-113">Parent Elements</span></span>

|<span data-ttu-id="d695d-114">元素</span><span class="sxs-lookup"><span data-stu-id="d695d-114">Element</span></span>|<span data-ttu-id="d695d-115">描述</span><span class="sxs-lookup"><span data-stu-id="d695d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d695d-116">檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d695d-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="d695d-117">定義必須存在的條件，才能使用控制項定義。</span><span class="sxs-lookup"><span data-stu-id="d695d-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d695d-118">文字值</span><span class="sxs-lookup"><span data-stu-id="d695d-118">Text Value</span></span>

<span data-ttu-id="d695d-119">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。</span><span class="sxs-lookup"><span data-stu-id="d695d-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="d695d-120">備註</span><span class="sxs-lookup"><span data-stu-id="d695d-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="d695d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d695d-121">See Also</span></span>

[<span data-ttu-id="d695d-122">檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d695d-122">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="d695d-123">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="d695d-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
