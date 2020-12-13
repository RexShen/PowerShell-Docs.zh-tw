---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl 之 WideItem 的 ScriptBlock 元素 (格式)
description: WideControl 之 WideItem 的 ScriptBlock 元素 (格式)
ms.openlocfilehash: 68e47926e5e6b846c8a0a3dbc16d1f0d59f11dee
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659876"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="edc20-103">WideControl 之 WideItem 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="edc20-103">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="edc20-104">指定以寬視圖顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="edc20-104">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="edc20-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) WideControl 元素 (格式) WideEntries 元素 (格式) WideEntry 專案 (格式) 之 wideitem 專案 (格式) 之 wideitem (格式的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="edc20-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="edc20-106">語法</span><span class="sxs-lookup"><span data-stu-id="edc20-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="edc20-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="edc20-107">Attributes and Elements</span></span>

<span data-ttu-id="edc20-108">下列各節描述專案的屬性、子項目和父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="edc20-108">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="edc20-109">屬性</span><span class="sxs-lookup"><span data-stu-id="edc20-109">Attributes</span></span>

<span data-ttu-id="edc20-110">無。</span><span class="sxs-lookup"><span data-stu-id="edc20-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="edc20-111">子元素</span><span class="sxs-lookup"><span data-stu-id="edc20-111">Child Elements</span></span>

<span data-ttu-id="edc20-112">無。</span><span class="sxs-lookup"><span data-stu-id="edc20-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="edc20-113">父項目</span><span class="sxs-lookup"><span data-stu-id="edc20-113">Parent Elements</span></span>

|<span data-ttu-id="edc20-114">元素</span><span class="sxs-lookup"><span data-stu-id="edc20-114">Element</span></span>|<span data-ttu-id="edc20-115">描述</span><span class="sxs-lookup"><span data-stu-id="edc20-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="edc20-116">之 wideitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="edc20-116">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="edc20-117">定義其值顯示在寬視圖中的屬性或腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="edc20-117">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="edc20-118">文字值</span><span class="sxs-lookup"><span data-stu-id="edc20-118">Text Value</span></span>

<span data-ttu-id="edc20-119">指定顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="edc20-119">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="edc20-120">備註</span><span class="sxs-lookup"><span data-stu-id="edc20-120">Remarks</span></span>

<span data-ttu-id="edc20-121">如需有關廣泛視圖元件的詳細資訊，請參閱 [建立廣泛的視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="edc20-121">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="edc20-122">範例</span><span class="sxs-lookup"><span data-stu-id="edc20-122">Example</span></span>

<span data-ttu-id="edc20-123">這個範例會示範 `WideItem` 定義腳本的元素，此腳本會在 view 中顯示其值。</span><span class="sxs-lookup"><span data-stu-id="edc20-123">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="edc20-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="edc20-124">See Also</span></span>

[<span data-ttu-id="edc20-125">之 wideitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="edc20-125">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="edc20-126">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="edc20-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="edc20-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="edc20-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
