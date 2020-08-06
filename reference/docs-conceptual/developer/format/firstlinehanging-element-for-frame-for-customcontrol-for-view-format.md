---
title: CustomControl for View (格式) 的框架的 FirstLineHanging 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: fa428c1fbe4cd8070e40cf0bc732eb335489ba4e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773635"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="0810a-102">檢視之 CustomControl 的框架的 FirstLineHanging 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0810a-102">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="0810a-103">指定第一行資料向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="0810a-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="0810a-104">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="0810a-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="0810a-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 專案 (格式) CustomEntries 元素用於 CustomControl for view (format) CustomEntry 元素 for CustomEntries for CustomItem for view (format) CustomEntry 專案 for CustomControlView for view (format) CustomItem 元素 for (格式) </span><span class="sxs-lookup"><span data-stu-id="0810a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0810a-106">語法</span><span class="sxs-lookup"><span data-stu-id="0810a-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0810a-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0810a-107">Attributes and Elements</span></span>

<span data-ttu-id="0810a-108">下列各節描述元素的屬性、子專案和父項目 `FirstLineHanging` 。</span><span class="sxs-lookup"><span data-stu-id="0810a-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0810a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="0810a-109">Attributes</span></span>

<span data-ttu-id="0810a-110">無。</span><span class="sxs-lookup"><span data-stu-id="0810a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0810a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="0810a-111">Child Elements</span></span>

<span data-ttu-id="0810a-112">無。</span><span class="sxs-lookup"><span data-stu-id="0810a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0810a-113">父項目</span><span class="sxs-lookup"><span data-stu-id="0810a-113">Parent Elements</span></span>

|<span data-ttu-id="0810a-114">元素</span><span class="sxs-lookup"><span data-stu-id="0810a-114">Element</span></span>|<span data-ttu-id="0810a-115">描述</span><span class="sxs-lookup"><span data-stu-id="0810a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0810a-116">檢視之 CustomControl 的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0810a-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="0810a-117">定義資料的顯示方式，例如將資料向左或向右移位。</span><span class="sxs-lookup"><span data-stu-id="0810a-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0810a-118">文字值</span><span class="sxs-lookup"><span data-stu-id="0810a-118">Text Value</span></span>

<span data-ttu-id="0810a-119">指定您想要將資料行移到第一行的字元數。</span><span class="sxs-lookup"><span data-stu-id="0810a-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="0810a-120">備註</span><span class="sxs-lookup"><span data-stu-id="0810a-120">Remarks</span></span>

<span data-ttu-id="0810a-121">如果指定這個元素，您就不能指定[FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="0810a-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="0810a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0810a-122">See Also</span></span>

[<span data-ttu-id="0810a-123">檢視之 CustomControl 的框架的 FirstLineIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0810a-123">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0810a-124">檢視之 CustomControl 的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="0810a-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0810a-125">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="0810a-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
