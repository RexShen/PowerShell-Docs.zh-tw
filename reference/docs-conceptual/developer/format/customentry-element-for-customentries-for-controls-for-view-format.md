---
title: View (Format) 的控制項之 CustomEntries 的 CustomEntry 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4fc960ab803580f684ce0f224b1db4d7d4af1720
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785892"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="570cb-102">檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="570cb-102">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="570cb-103">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="570cb-103">Provides a definition of the control.</span></span> <span data-ttu-id="570cb-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="570cb-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="570cb-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 CustomControl 格式 (格式的控制項的 CustomEntries 專案) 格式 (CustomEntry 元素用於 view) 格式的控制項 (CustomEntries 專案</span><span class="sxs-lookup"><span data-stu-id="570cb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="570cb-106">語法</span><span class="sxs-lookup"><span data-stu-id="570cb-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="570cb-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="570cb-107">Attributes and Elements</span></span>

<span data-ttu-id="570cb-108">下列各節說明屬性、子專案和元素的父元素 `CustomEntry` 。</span><span class="sxs-lookup"><span data-stu-id="570cb-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="570cb-109">屬性</span><span class="sxs-lookup"><span data-stu-id="570cb-109">Attributes</span></span>

<span data-ttu-id="570cb-110">無。</span><span class="sxs-lookup"><span data-stu-id="570cb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="570cb-111">子元素</span><span class="sxs-lookup"><span data-stu-id="570cb-111">Child Elements</span></span>

|<span data-ttu-id="570cb-112">元素</span><span class="sxs-lookup"><span data-stu-id="570cb-112">Element</span></span>|<span data-ttu-id="570cb-113">描述</span><span class="sxs-lookup"><span data-stu-id="570cb-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="570cb-114">檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="570cb-114">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="570cb-115">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="570cb-115">Optional element.</span></span><br /><br /> <span data-ttu-id="570cb-116">定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。</span><span class="sxs-lookup"><span data-stu-id="570cb-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="570cb-117">檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="570cb-117">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="570cb-118">必要元素。</span><span class="sxs-lookup"><span data-stu-id="570cb-118">Required element.</span></span><br /><br /> <span data-ttu-id="570cb-119">定義控制項顯示資料的方式。</span><span class="sxs-lookup"><span data-stu-id="570cb-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="570cb-120">父項目</span><span class="sxs-lookup"><span data-stu-id="570cb-120">Parent Elements</span></span>

|<span data-ttu-id="570cb-121">元素</span><span class="sxs-lookup"><span data-stu-id="570cb-121">Element</span></span>|<span data-ttu-id="570cb-122">描述</span><span class="sxs-lookup"><span data-stu-id="570cb-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="570cb-123">檢視之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="570cb-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="570cb-124">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="570cb-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="570cb-125">備註</span><span class="sxs-lookup"><span data-stu-id="570cb-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="570cb-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="570cb-126">See Also</span></span>

[<span data-ttu-id="570cb-127">檢視之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="570cb-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="570cb-128">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="570cb-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
