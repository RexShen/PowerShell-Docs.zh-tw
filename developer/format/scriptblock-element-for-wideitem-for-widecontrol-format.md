---
title: WideItem WideControl （格式） 的指令碼區塊項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064198"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="1e39e-102">WideControl 之 WideItem 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="1e39e-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="1e39e-103">指定其值會顯示在寬型檢視的指令碼。</span><span class="sxs-lookup"><span data-stu-id="1e39e-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="1e39e-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry 項目 （格式） WideItem 項目 （格式） 指令碼區塊項目 WideItem （格式）</span><span class="sxs-lookup"><span data-stu-id="1e39e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1e39e-105">語法</span><span class="sxs-lookup"><span data-stu-id="1e39e-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1e39e-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1e39e-106">Attributes and Elements</span></span>

<span data-ttu-id="1e39e-107">下列各節說明屬性、 子項目和父項目`ScriptBlock`項目。</span><span class="sxs-lookup"><span data-stu-id="1e39e-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1e39e-108">屬性</span><span class="sxs-lookup"><span data-stu-id="1e39e-108">Attributes</span></span>

<span data-ttu-id="1e39e-109">無。</span><span class="sxs-lookup"><span data-stu-id="1e39e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1e39e-110">子元素</span><span class="sxs-lookup"><span data-stu-id="1e39e-110">Child Elements</span></span>

<span data-ttu-id="1e39e-111">無。</span><span class="sxs-lookup"><span data-stu-id="1e39e-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1e39e-112">父項目</span><span class="sxs-lookup"><span data-stu-id="1e39e-112">Parent Elements</span></span>

|<span data-ttu-id="1e39e-113">項目</span><span class="sxs-lookup"><span data-stu-id="1e39e-113">Element</span></span>|<span data-ttu-id="1e39e-114">描述</span><span class="sxs-lookup"><span data-stu-id="1e39e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1e39e-115">WideItem 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="1e39e-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="1e39e-116">定義在寬型檢視中顯示其值的屬性或指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="1e39e-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1e39e-117">文字值</span><span class="sxs-lookup"><span data-stu-id="1e39e-117">Text Value</span></span>

<span data-ttu-id="1e39e-118">指定其值會顯示指令碼。</span><span class="sxs-lookup"><span data-stu-id="1e39e-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="1e39e-119">備註</span><span class="sxs-lookup"><span data-stu-id="1e39e-119">Remarks</span></span>

<span data-ttu-id="1e39e-120">如需詳細的寬型檢視元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="1e39e-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1e39e-121">範例</span><span class="sxs-lookup"><span data-stu-id="1e39e-121">Example</span></span>

<span data-ttu-id="1e39e-122">此範例示範`WideItem`項目，定義其值會顯示在檢視指令碼。</span><span class="sxs-lookup"><span data-stu-id="1e39e-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="1e39e-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e39e-123">See Also</span></span>

[<span data-ttu-id="1e39e-124">WideItem 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="1e39e-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="1e39e-125">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="1e39e-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="1e39e-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="1e39e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
