---
title: CustomControl for View 的 Frame 的 FirstLineIndent 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 3130ecc69f7d1568bcbd392dd24e8cdcc3382905
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363057"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="d5a0c-102">檢視之 CustomControl 的框架的 FirstLineIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="d5a0c-102">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="d5a0c-103">指定第一行資料向右移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="d5a0c-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="d5a0c-104">定義自訂控制項視圖時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="d5a0c-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="d5a0c-105">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素（format） CustomEntries 元素，用於 CustomEntry for View （Format） CustomEntries 元素的 CustomControl for view （format） CustomItem 元素CustomItem for CustomControl for View （Format） FirstLineIndent 元素的 CustomEntry for CustomControlView （Format） Frame 元素</span><span class="sxs-lookup"><span data-stu-id="d5a0c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineIndent Element</span></span>

## <a name="syntax"></a><span data-ttu-id="d5a0c-106">語法</span><span class="sxs-lookup"><span data-stu-id="d5a0c-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d5a0c-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="d5a0c-107">Attributes and Elements</span></span>

<span data-ttu-id="d5a0c-108">下列各節描述 `FirstLineIndent` 元素的屬性、子專案和父項目。</span><span class="sxs-lookup"><span data-stu-id="d5a0c-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d5a0c-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d5a0c-109">Attributes</span></span>

<span data-ttu-id="d5a0c-110">無。</span><span class="sxs-lookup"><span data-stu-id="d5a0c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d5a0c-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d5a0c-111">Child Elements</span></span>

<span data-ttu-id="d5a0c-112">無。</span><span class="sxs-lookup"><span data-stu-id="d5a0c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d5a0c-113">父元素</span><span class="sxs-lookup"><span data-stu-id="d5a0c-113">Parent Elements</span></span>

|<span data-ttu-id="d5a0c-114">元素</span><span class="sxs-lookup"><span data-stu-id="d5a0c-114">Element</span></span>|<span data-ttu-id="d5a0c-115">描述</span><span class="sxs-lookup"><span data-stu-id="d5a0c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d5a0c-116">適用于 CustomControl for View 的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d5a0c-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="d5a0c-117">定義資料的顯示方式，例如將資料向左或向右移位。</span><span class="sxs-lookup"><span data-stu-id="d5a0c-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d5a0c-118">文字值</span><span class="sxs-lookup"><span data-stu-id="d5a0c-118">Text Value</span></span>

<span data-ttu-id="d5a0c-119">指定您想要將資料行移到第一行的字元數。</span><span class="sxs-lookup"><span data-stu-id="d5a0c-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="d5a0c-120">備註</span><span class="sxs-lookup"><span data-stu-id="d5a0c-120">Remarks</span></span>

<span data-ttu-id="d5a0c-121">如果指定這個元素，您就不能指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="d5a0c-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="d5a0c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5a0c-122">See Also</span></span>

[<span data-ttu-id="d5a0c-123">CustomControl for View 的 Frame 的 FirstLineHanging 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d5a0c-123">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d5a0c-124">適用于 CustomControl for View 的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d5a0c-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d5a0c-125">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="d5a0c-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
