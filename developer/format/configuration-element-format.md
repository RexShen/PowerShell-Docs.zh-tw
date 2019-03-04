---
title: 組態項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856324"
---
# <a name="configuration-element-format"></a><span data-ttu-id="c1463-102">設定元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="c1463-102">Configuration Element (Format)</span></span>

<span data-ttu-id="c1463-103">表示格式化檔案的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="c1463-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="c1463-104">組態項目</span><span class="sxs-lookup"><span data-stu-id="c1463-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="c1463-105">語法</span><span class="sxs-lookup"><span data-stu-id="c1463-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c1463-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="c1463-106">Attributes and Elements</span></span>

<span data-ttu-id="c1463-107">下列各節說明屬性、 子項目和父項目`Configuration`項目。</span><span class="sxs-lookup"><span data-stu-id="c1463-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="c1463-108">此元素必須是每個格式檔案的根項目及這個項目必須包含至少一個子項目。</span><span class="sxs-lookup"><span data-stu-id="c1463-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c1463-109">屬性</span><span class="sxs-lookup"><span data-stu-id="c1463-109">Attributes</span></span>

<span data-ttu-id="c1463-110">無。</span><span class="sxs-lookup"><span data-stu-id="c1463-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c1463-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c1463-111">Child Elements</span></span>

|<span data-ttu-id="c1463-112">元素</span><span class="sxs-lookup"><span data-stu-id="c1463-112">Element</span></span>|<span data-ttu-id="c1463-113">描述</span><span class="sxs-lookup"><span data-stu-id="c1463-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1463-114">組態 （格式） 的 controls 項目</span><span class="sxs-lookup"><span data-stu-id="c1463-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="c1463-115">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="c1463-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c1463-116">定義可由格式檔案的所有檢視通用控制項。</span><span class="sxs-lookup"><span data-stu-id="c1463-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="c1463-117">DefaultSettings 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="c1463-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="c1463-118">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="c1463-118">Optional element.</span></span><br /><br /> <span data-ttu-id="c1463-119">定義套用至的格式化檔案的所有檢視的常見設定。</span><span class="sxs-lookup"><span data-stu-id="c1463-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="c1463-120">SelectionSets 項目格式</span><span class="sxs-lookup"><span data-stu-id="c1463-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="c1463-121">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="c1463-121">Optional element.</span></span><br /><br /> <span data-ttu-id="c1463-122">定義通用的集合，可供所有檢視的格式化檔案的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="c1463-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="c1463-123">ViewDefinitions 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="c1463-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="c1463-124">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="c1463-124">Optional element.</span></span><br /><br /> <span data-ttu-id="c1463-125">定義用來顯示物件的檢視。</span><span class="sxs-lookup"><span data-stu-id="c1463-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c1463-126">父元素</span><span class="sxs-lookup"><span data-stu-id="c1463-126">Parent Elements</span></span>

<span data-ttu-id="c1463-127">無。</span><span class="sxs-lookup"><span data-stu-id="c1463-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="c1463-128">備註</span><span class="sxs-lookup"><span data-stu-id="c1463-128">Remarks</span></span>

<span data-ttu-id="c1463-129">格式檔案會定義物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="c1463-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="c1463-130">在大部分情況下，此根項目包含[ViewDefinitions](./viewdefinitions-element-format.md)定義資料表、 清單和格式檔案的寬型檢視的項目。</span><span class="sxs-lookup"><span data-stu-id="c1463-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="c1463-131">檢視定義中，除了一般的選取項目集、 設定和這些檢視可以使用的控制項，可以定義的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="c1463-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1463-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1463-132">See Also</span></span>

[<span data-ttu-id="c1463-133">組態 （格式） 的 controls 項目</span><span class="sxs-lookup"><span data-stu-id="c1463-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="c1463-134">DefaultSettings 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="c1463-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="c1463-135">SelectionSets 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="c1463-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="c1463-136">ViewDefinitions 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="c1463-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="c1463-137">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="c1463-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
