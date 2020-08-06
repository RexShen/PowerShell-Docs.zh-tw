---
title: GroupBy (格式) 的 CustomItem 框架元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1568236ff7b6142f7e41be70a3ae5e28307cf790
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785756"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="583fb-102">GroupBy 之 CustomItem 的框架元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="583fb-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="583fb-103">定義資料的顯示方式，例如將資料向左或向右移位。</span><span class="sxs-lookup"><span data-stu-id="583fb-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="583fb-104">此元素是在定義新物件群組的顯示方式時使用。</span><span class="sxs-lookup"><span data-stu-id="583fb-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="583fb-105">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素（GroupBy (格式）) CustomEntries 專案（適用于 CustomEntry 的 groupby (格式)  (CustomControl 元素，CustomItem 的 groupby) 格式 (CustomEntry 元素) 的專案。</span><span class="sxs-lookup"><span data-stu-id="583fb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="583fb-106">語法</span><span class="sxs-lookup"><span data-stu-id="583fb-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="583fb-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="583fb-107">Attributes and Elements</span></span>

<span data-ttu-id="583fb-108">下列各節說明屬性、子專案和元素的父元素 `Frame` 。</span><span class="sxs-lookup"><span data-stu-id="583fb-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="583fb-109">屬性</span><span class="sxs-lookup"><span data-stu-id="583fb-109">Attributes</span></span>

<span data-ttu-id="583fb-110">無。</span><span class="sxs-lookup"><span data-stu-id="583fb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="583fb-111">子元素</span><span class="sxs-lookup"><span data-stu-id="583fb-111">Child Elements</span></span>

|<span data-ttu-id="583fb-112">元素</span><span class="sxs-lookup"><span data-stu-id="583fb-112">Element</span></span>|<span data-ttu-id="583fb-113">描述</span><span class="sxs-lookup"><span data-stu-id="583fb-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="583fb-114">必要元素</span><span class="sxs-lookup"><span data-stu-id="583fb-114">Required Element</span></span>|
|[<span data-ttu-id="583fb-115">GroupBy 之框架的 FirstLineHanging 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="583fb-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="583fb-116">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="583fb-116">Optional element.</span></span><br /><br /> <span data-ttu-id="583fb-117">指定第一行資料向左移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="583fb-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="583fb-118">GroupBy 之框架的 FirstLineIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="583fb-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="583fb-119">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="583fb-119">Optional element.</span></span><br /><br /> <span data-ttu-id="583fb-120">指定第一行資料向右移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="583fb-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="583fb-121">GroupBy 之框架的 LeftIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="583fb-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="583fb-122">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="583fb-122">Optional element.</span></span><br /><br /> <span data-ttu-id="583fb-123">指定資料從左邊界下移的字元數。</span><span class="sxs-lookup"><span data-stu-id="583fb-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="583fb-124">[GroupBy (格式之框架的 RightIndent 元素) ](./rightindent-element-for-frame-for-groupby-format.md)RightIndent 元素</span><span class="sxs-lookup"><span data-stu-id="583fb-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="583fb-125">選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="583fb-125">Optional element.</span></span><br /><br /> <span data-ttu-id="583fb-126">指定資料從右邊界向外移動的字元數。</span><span class="sxs-lookup"><span data-stu-id="583fb-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="583fb-127">父項目</span><span class="sxs-lookup"><span data-stu-id="583fb-127">Parent Elements</span></span>

|<span data-ttu-id="583fb-128">元素</span><span class="sxs-lookup"><span data-stu-id="583fb-128">Element</span></span>|<span data-ttu-id="583fb-129">描述</span><span class="sxs-lookup"><span data-stu-id="583fb-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="583fb-130">GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="583fb-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="583fb-131">定義控制項所顯示的資料及其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="583fb-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="583fb-132">備註</span><span class="sxs-lookup"><span data-stu-id="583fb-132">Remarks</span></span>

<span data-ttu-id="583fb-133">您不能在相同的專案中指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md)和[FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md)元素 `Frame` 。</span><span class="sxs-lookup"><span data-stu-id="583fb-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="583fb-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="583fb-134">See Also</span></span>

[<span data-ttu-id="583fb-135">GroupBy 之框架的 FirstLineHanging 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="583fb-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="583fb-136">GroupBy 之框架的 FirstLineIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="583fb-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="583fb-137">GroupBy 之框架的 LeftIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="583fb-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="583fb-138">GroupBy 之框架的 RightIndent 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="583fb-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="583fb-139">GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="583fb-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="583fb-140">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="583fb-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
