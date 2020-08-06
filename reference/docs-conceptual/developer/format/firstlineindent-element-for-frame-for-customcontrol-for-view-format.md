---
title: CustomControl for View (格式) 的框架的 FirstLineIndent 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0d51be5b5fc04bc0ea8442ca96767b1d9d8473a4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785807"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="29280-102">檢視之 CustomControl 的框架的 FirstLineIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="29280-102">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="29280-103">指定第一行資料向右移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="29280-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="29280-104">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="29280-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="29280-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 專案 (格式) CustomControl for view (CustomEntry 元素，CustomEntries for view) format (CustomItem 專案（CustomEntry 的 CustomControlView for view) CustomItem 元素的 CustomControl (格式) FirstLineIndent 元素</span><span class="sxs-lookup"><span data-stu-id="29280-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineIndent Element</span></span>

## <a name="syntax"></a><span data-ttu-id="29280-106">語法</span><span class="sxs-lookup"><span data-stu-id="29280-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="29280-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="29280-107">Attributes and Elements</span></span>

<span data-ttu-id="29280-108">下列各節描述元素的屬性、子專案和父項目 `FirstLineIndent` 。</span><span class="sxs-lookup"><span data-stu-id="29280-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="29280-109">屬性</span><span class="sxs-lookup"><span data-stu-id="29280-109">Attributes</span></span>

<span data-ttu-id="29280-110">無。</span><span class="sxs-lookup"><span data-stu-id="29280-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="29280-111">子元素</span><span class="sxs-lookup"><span data-stu-id="29280-111">Child Elements</span></span>

<span data-ttu-id="29280-112">無。</span><span class="sxs-lookup"><span data-stu-id="29280-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="29280-113">父項目</span><span class="sxs-lookup"><span data-stu-id="29280-113">Parent Elements</span></span>

|<span data-ttu-id="29280-114">元素</span><span class="sxs-lookup"><span data-stu-id="29280-114">Element</span></span>|<span data-ttu-id="29280-115">描述</span><span class="sxs-lookup"><span data-stu-id="29280-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="29280-116">檢視之 CustomControl 的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="29280-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="29280-117">定義資料的顯示方式，例如將資料向左或向右移位。</span><span class="sxs-lookup"><span data-stu-id="29280-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="29280-118">文字值</span><span class="sxs-lookup"><span data-stu-id="29280-118">Text Value</span></span>

<span data-ttu-id="29280-119">指定您想要將資料行移到第一行的字元數。</span><span class="sxs-lookup"><span data-stu-id="29280-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="29280-120">備註</span><span class="sxs-lookup"><span data-stu-id="29280-120">Remarks</span></span>

<span data-ttu-id="29280-121">如果指定這個元素，您就不能指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="29280-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="29280-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29280-122">See Also</span></span>

[<span data-ttu-id="29280-123">檢視之 CustomControl 的框架的 FirstLineHanging 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="29280-123">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="29280-124">檢視之 CustomControl 的 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="29280-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="29280-125">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="29280-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
