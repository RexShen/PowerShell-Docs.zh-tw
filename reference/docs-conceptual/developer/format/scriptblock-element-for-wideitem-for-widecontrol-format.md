---
title: 之 wideitem for WideControl (格式的 ScriptBlock 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: be649d6de0d2dfa6bad14f2d7476cced9cd6cb6d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787592"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="042fb-102">WideControl 之 WideItem 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="042fb-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="042fb-103">指定在寬視圖中顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="042fb-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="042fb-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 專案 (格式) WideEntries 專案 (格式) WideEntry 元素 (格式) 之 wideitem 元素 (格式) 之 wideitem (格式的 ScriptBlock 元素) </span><span class="sxs-lookup"><span data-stu-id="042fb-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="042fb-105">語法</span><span class="sxs-lookup"><span data-stu-id="042fb-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="042fb-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="042fb-106">Attributes and Elements</span></span>

<span data-ttu-id="042fb-107">下列各節描述元素的屬性、子專案和父項目 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="042fb-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="042fb-108">屬性</span><span class="sxs-lookup"><span data-stu-id="042fb-108">Attributes</span></span>

<span data-ttu-id="042fb-109">無。</span><span class="sxs-lookup"><span data-stu-id="042fb-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="042fb-110">子元素</span><span class="sxs-lookup"><span data-stu-id="042fb-110">Child Elements</span></span>

<span data-ttu-id="042fb-111">無。</span><span class="sxs-lookup"><span data-stu-id="042fb-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="042fb-112">父項目</span><span class="sxs-lookup"><span data-stu-id="042fb-112">Parent Elements</span></span>

|<span data-ttu-id="042fb-113">元素</span><span class="sxs-lookup"><span data-stu-id="042fb-113">Element</span></span>|<span data-ttu-id="042fb-114">描述</span><span class="sxs-lookup"><span data-stu-id="042fb-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="042fb-115">之 wideitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="042fb-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="042fb-116">定義屬性或腳本區塊，其值會顯示在寬視圖中。</span><span class="sxs-lookup"><span data-stu-id="042fb-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="042fb-117">文字值</span><span class="sxs-lookup"><span data-stu-id="042fb-117">Text Value</span></span>

<span data-ttu-id="042fb-118">指定顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="042fb-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="042fb-119">備註</span><span class="sxs-lookup"><span data-stu-id="042fb-119">Remarks</span></span>

<span data-ttu-id="042fb-120">如需有關寬視圖元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="042fb-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="042fb-121">範例</span><span class="sxs-lookup"><span data-stu-id="042fb-121">Example</span></span>

<span data-ttu-id="042fb-122">這個範例示範的 `WideItem` 元素會定義一個腳本，其值會顯示在視圖中。</span><span class="sxs-lookup"><span data-stu-id="042fb-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="042fb-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="042fb-123">See Also</span></span>

[<span data-ttu-id="042fb-124">之 wideitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="042fb-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="042fb-125">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="042fb-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="042fb-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="042fb-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
