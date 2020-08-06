---
title: View (Format) 的控制項之框架的 FirstLineIndent 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d3927be2cdce24b65b4d94dfb17ae57a1b47270c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773516"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-view-format"></a><span data-ttu-id="dff1b-102">檢視之控制項的框架的 FirstLineIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dff1b-102">FirstLineIndent Element for Frame for Controls for View (Format)</span></span>

<span data-ttu-id="dff1b-103">指定第一行資料向右移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="dff1b-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="dff1b-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="dff1b-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="dff1b-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 CustomControl， (格式控制項的控制項) CustomEntries 元素用於 view (格式) CustomEntries 的控制項適用于 view (Format) CustomItem 元素的 CustomEntry for view (Format) Frame 元素 for view (format) CustomItem 元素的控制項 (格式的控制項</span><span class="sxs-lookup"><span data-stu-id="dff1b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format) FirstLineIndent Element of Frame of Controls of View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dff1b-106">語法</span><span class="sxs-lookup"><span data-stu-id="dff1b-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dff1b-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dff1b-107">Attributes and Elements</span></span>

<span data-ttu-id="dff1b-108">下列各節描述元素的屬性、子專案和父項目 `FirstLineIndent` 。</span><span class="sxs-lookup"><span data-stu-id="dff1b-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dff1b-109">屬性</span><span class="sxs-lookup"><span data-stu-id="dff1b-109">Attributes</span></span>

<span data-ttu-id="dff1b-110">無。</span><span class="sxs-lookup"><span data-stu-id="dff1b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dff1b-111">子元素</span><span class="sxs-lookup"><span data-stu-id="dff1b-111">Child Elements</span></span>

<span data-ttu-id="dff1b-112">無。</span><span class="sxs-lookup"><span data-stu-id="dff1b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dff1b-113">父項目</span><span class="sxs-lookup"><span data-stu-id="dff1b-113">Parent Elements</span></span>

|<span data-ttu-id="dff1b-114">元素</span><span class="sxs-lookup"><span data-stu-id="dff1b-114">Element</span></span>|<span data-ttu-id="dff1b-115">描述</span><span class="sxs-lookup"><span data-stu-id="dff1b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dff1b-116">檢視之控制項的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dff1b-116">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="dff1b-117">定義資料的顯示方式，例如將資料向左或向右移位。</span><span class="sxs-lookup"><span data-stu-id="dff1b-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dff1b-118">文字值</span><span class="sxs-lookup"><span data-stu-id="dff1b-118">Text Value</span></span>

<span data-ttu-id="dff1b-119">指定您想要將資料行移到第一行的字元數。</span><span class="sxs-lookup"><span data-stu-id="dff1b-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="dff1b-120">備註</span><span class="sxs-lookup"><span data-stu-id="dff1b-120">Remarks</span></span>

<span data-ttu-id="dff1b-121">如果指定這個元素，您就不能指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="dff1b-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="dff1b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dff1b-122">See Also</span></span>

[<span data-ttu-id="dff1b-123">檢視之控制項的框架的 FirstLineHanging 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dff1b-123">FirstLineHanging Element for Frame for Controls for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="dff1b-124">檢視之控制項的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="dff1b-124">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="dff1b-125">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="dff1b-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
