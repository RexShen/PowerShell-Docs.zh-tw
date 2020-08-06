---
title: " (格式) 設定之控制項的框架的 FirstLineHanging 元素 |Microsoft Docs"
ms.date: 09/13/2016
ms.openlocfilehash: 6c0429a5caa5d20370acff72fa5707ed8cf7ad01
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773737"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="d981a-102">設定之控制項的框架的 FirstLineHanging 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d981a-102">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="d981a-103">指定第一行資料向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="d981a-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="d981a-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="d981a-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="d981a-105">Configuration 元素 (格式) Controls 設定的控制項元素 (格式設定的控制項) 控制項專案 (格式) 設定 (格式的 CustomControl 的 CustomEntries 元素) CustomEntry 元素如需設定 (格式的控制項的 CustomControl) CustomItem 元素用於 CustomEntry 的設定框架元素 CustomItem 的控制項設定 (格式的控制項) FirstLineHanging 元素)  (</span><span class="sxs-lookup"><span data-stu-id="d981a-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d981a-106">語法</span><span class="sxs-lookup"><span data-stu-id="d981a-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d981a-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d981a-107">Attributes and Elements</span></span>

<span data-ttu-id="d981a-108">下列各節描述元素的屬性、子專案和父項目 `FirstLineHanging` 。</span><span class="sxs-lookup"><span data-stu-id="d981a-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d981a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d981a-109">Attributes</span></span>

<span data-ttu-id="d981a-110">無。</span><span class="sxs-lookup"><span data-stu-id="d981a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d981a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d981a-111">Child Elements</span></span>

<span data-ttu-id="d981a-112">無。</span><span class="sxs-lookup"><span data-stu-id="d981a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d981a-113">父項目</span><span class="sxs-lookup"><span data-stu-id="d981a-113">Parent Elements</span></span>

|<span data-ttu-id="d981a-114">元素</span><span class="sxs-lookup"><span data-stu-id="d981a-114">Element</span></span>|<span data-ttu-id="d981a-115">描述</span><span class="sxs-lookup"><span data-stu-id="d981a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d981a-116">設定之控制項的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d981a-116">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="d981a-117">定義資料的顯示方式，例如將資料向左或向右移位。</span><span class="sxs-lookup"><span data-stu-id="d981a-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d981a-118">文字值</span><span class="sxs-lookup"><span data-stu-id="d981a-118">Text Value</span></span>

<span data-ttu-id="d981a-119">指定您想要將資料行移到第一行的字元數。</span><span class="sxs-lookup"><span data-stu-id="d981a-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="d981a-120">備註</span><span class="sxs-lookup"><span data-stu-id="d981a-120">Remarks</span></span>

<span data-ttu-id="d981a-121">如果指定這個元素，則無法指定 `FirstLineIndent` 元素。</span><span class="sxs-lookup"><span data-stu-id="d981a-121">If this element is specified, you cannot specify the `FirstLineIndent` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="d981a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d981a-122">See Also</span></span>

[<span data-ttu-id="d981a-123">設定之控制項的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d981a-123">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="d981a-124">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="d981a-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
