---
title: 設定 (格式) 之控制項的之 entryselectedby 的 TypeName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 994cd368872392abe47b4e9422c661cd8c03e05c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783342"
---
# <a name="typename-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="5ada2-102">設定之控制項的 EntrySelectedBy 的 TypeName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5ada2-102">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="5ada2-103">指定使用此控制項定義的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="5ada2-103">Specifies a .NET type that uses this definition of the control.</span></span> <span data-ttu-id="5ada2-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="5ada2-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="5ada2-105">Configuration 專案 (格式) Controls 設定的控制項元素 (格式設定的控制項) 控制項專案 (格式) 設定 (格式的 CustomControl 的 CustomControl 元素 CustomControl 的設定)  (格式) 之 entryselectedby 元素 ()  ()  (格式設定的控制項的 CustomEntry 專案的之 entryselectedby for configuration) 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="5ada2-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5ada2-106">語法</span><span class="sxs-lookup"><span data-stu-id="5ada2-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="5ada2-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5ada2-107">Attributes and Elements</span></span>

<span data-ttu-id="5ada2-108">下列各節說明屬性、子專案和元素的父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="5ada2-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5ada2-109">屬性</span><span class="sxs-lookup"><span data-stu-id="5ada2-109">Attributes</span></span>

<span data-ttu-id="5ada2-110">無。</span><span class="sxs-lookup"><span data-stu-id="5ada2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5ada2-111">子元素</span><span class="sxs-lookup"><span data-stu-id="5ada2-111">Child Elements</span></span>

<span data-ttu-id="5ada2-112">無。</span><span class="sxs-lookup"><span data-stu-id="5ada2-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5ada2-113">父項目</span><span class="sxs-lookup"><span data-stu-id="5ada2-113">Parent Elements</span></span>

|<span data-ttu-id="5ada2-114">元素</span><span class="sxs-lookup"><span data-stu-id="5ada2-114">Element</span></span>|<span data-ttu-id="5ada2-115">描述</span><span class="sxs-lookup"><span data-stu-id="5ada2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ada2-116">設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5ada2-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="5ada2-117">定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="5ada2-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5ada2-118">文字值</span><span class="sxs-lookup"><span data-stu-id="5ada2-118">Text Value</span></span>

<span data-ttu-id="5ada2-119">指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。</span><span class="sxs-lookup"><span data-stu-id="5ada2-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ada2-120">備註</span><span class="sxs-lookup"><span data-stu-id="5ada2-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="5ada2-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ada2-121">See Also</span></span>

[<span data-ttu-id="5ada2-122">設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="5ada2-122">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="5ada2-123">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="5ada2-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
