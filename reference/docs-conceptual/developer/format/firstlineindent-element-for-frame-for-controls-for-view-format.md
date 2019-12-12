---
title: View 之控制項的框架的 FirstLineIndent 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec63f4f9-8858-4529-8646-ffbbc278f83e
caps.latest.revision: 7
ms.openlocfilehash: 694c5baaa5e90a772257276ba139d90acf7ec0e3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363087"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-view-format"></a><span data-ttu-id="43c04-102">檢視之控制項的框架的 FirstLineIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="43c04-102">FirstLineIndent Element for Frame for Controls for View (Format)</span></span>

<span data-ttu-id="43c04-103">指定第一行資料向右移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="43c04-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="43c04-104">定義可供視圖使用的控制項時，會使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="43c04-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="43c04-105">設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素CustomControl for View （format） CustomEntry 元素 for CustomEntries for view （format） CustomItem 元素 for view （format） CustomEntry for view （format） CustomItem 元素之控制項的 FirstLineIndentView 控制項的（格式）</span><span class="sxs-lookup"><span data-stu-id="43c04-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format) FirstLineIndent Element of Frame of Controls of View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="43c04-106">語法</span><span class="sxs-lookup"><span data-stu-id="43c04-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="43c04-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="43c04-107">Attributes and Elements</span></span>

<span data-ttu-id="43c04-108">下列各節描述 `FirstLineIndent` 元素的屬性、子專案和父項目。</span><span class="sxs-lookup"><span data-stu-id="43c04-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="43c04-109">屬性</span><span class="sxs-lookup"><span data-stu-id="43c04-109">Attributes</span></span>

<span data-ttu-id="43c04-110">無。</span><span class="sxs-lookup"><span data-stu-id="43c04-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="43c04-111">子元素</span><span class="sxs-lookup"><span data-stu-id="43c04-111">Child Elements</span></span>

<span data-ttu-id="43c04-112">無。</span><span class="sxs-lookup"><span data-stu-id="43c04-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="43c04-113">父元素</span><span class="sxs-lookup"><span data-stu-id="43c04-113">Parent Elements</span></span>

|<span data-ttu-id="43c04-114">元素</span><span class="sxs-lookup"><span data-stu-id="43c04-114">Element</span></span>|<span data-ttu-id="43c04-115">描述</span><span class="sxs-lookup"><span data-stu-id="43c04-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="43c04-116">View 之控制項的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="43c04-116">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="43c04-117">定義資料的顯示方式，例如將資料向左或向右移位。</span><span class="sxs-lookup"><span data-stu-id="43c04-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="43c04-118">文字值</span><span class="sxs-lookup"><span data-stu-id="43c04-118">Text Value</span></span>

<span data-ttu-id="43c04-119">指定您想要將資料行移到第一行的字元數。</span><span class="sxs-lookup"><span data-stu-id="43c04-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="43c04-120">備註</span><span class="sxs-lookup"><span data-stu-id="43c04-120">Remarks</span></span>

<span data-ttu-id="43c04-121">如果指定這個元素，您就不能指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="43c04-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="43c04-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43c04-122">See Also</span></span>

[<span data-ttu-id="43c04-123">View 之控制項的框架的 FirstLineHanging 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="43c04-123">FirstLineHanging Element for Frame for Controls for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="43c04-124">View 之控制項的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="43c04-124">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="43c04-125">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="43c04-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
