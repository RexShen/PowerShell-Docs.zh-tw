---
title: WideControl 之之 wideitem 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362027"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="7b675-102">WideControl 之 WideItem 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="7b675-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="7b675-103">指定在寬視圖中顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="7b675-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="7b675-104">之 wideitem 的設定元素（格式） ViewDefinitions 元素（格式） View 元素（format） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（格式）之 wideitem 元素（格式） ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7b675-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7b675-105">語法</span><span class="sxs-lookup"><span data-stu-id="7b675-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7b675-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="7b675-106">Attributes and Elements</span></span>

<span data-ttu-id="7b675-107">下列各節描述 `ScriptBlock` 專案的屬性、子專案和父項目。</span><span class="sxs-lookup"><span data-stu-id="7b675-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7b675-108">屬性</span><span class="sxs-lookup"><span data-stu-id="7b675-108">Attributes</span></span>

<span data-ttu-id="7b675-109">無。</span><span class="sxs-lookup"><span data-stu-id="7b675-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7b675-110">子元素</span><span class="sxs-lookup"><span data-stu-id="7b675-110">Child Elements</span></span>

<span data-ttu-id="7b675-111">無。</span><span class="sxs-lookup"><span data-stu-id="7b675-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7b675-112">父元素</span><span class="sxs-lookup"><span data-stu-id="7b675-112">Parent Elements</span></span>

|<span data-ttu-id="7b675-113">元素</span><span class="sxs-lookup"><span data-stu-id="7b675-113">Element</span></span>|<span data-ttu-id="7b675-114">描述</span><span class="sxs-lookup"><span data-stu-id="7b675-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7b675-115">之 wideitem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7b675-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="7b675-116">定義屬性或腳本區塊，其值會顯示在寬視圖中。</span><span class="sxs-lookup"><span data-stu-id="7b675-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7b675-117">文字值</span><span class="sxs-lookup"><span data-stu-id="7b675-117">Text Value</span></span>

<span data-ttu-id="7b675-118">指定顯示其值的腳本。</span><span class="sxs-lookup"><span data-stu-id="7b675-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="7b675-119">備註</span><span class="sxs-lookup"><span data-stu-id="7b675-119">Remarks</span></span>

<span data-ttu-id="7b675-120">如需有關寬視圖元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="7b675-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7b675-121">範例</span><span class="sxs-lookup"><span data-stu-id="7b675-121">Example</span></span>

<span data-ttu-id="7b675-122">這個範例會顯示一個 `WideItem` 專案，定義一個腳本，其值會顯示在視圖中。</span><span class="sxs-lookup"><span data-stu-id="7b675-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="7b675-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b675-123">See Also</span></span>

[<span data-ttu-id="7b675-124">之 wideitem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7b675-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="7b675-125">建立寬型視圖</span><span class="sxs-lookup"><span data-stu-id="7b675-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="7b675-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="7b675-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
