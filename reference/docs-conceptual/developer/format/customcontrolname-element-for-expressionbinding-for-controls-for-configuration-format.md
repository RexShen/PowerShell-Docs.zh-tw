---
title: 設定之控制項的 ExpressionBinding 的 CustomControlName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5242935-2782-4d23-84f5-2446b2b7ba83
caps.latest.revision: 8
ms.openlocfilehash: c9abd9f22907b87323c16d603a9f75bb3d375a03
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364117"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="34b24-102">設定之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="34b24-102">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="34b24-103">指定通用控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="34b24-103">Specifies the name of a common control.</span></span> <span data-ttu-id="34b24-104">此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。</span><span class="sxs-lookup"><span data-stu-id="34b24-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="34b24-105">Configuration 元素（格式）控制設定（format） CustomControl 元素的設定（格式）控制項專案的設定專案（格式） CustomControl 設定的 CustomEntries 元素（格式）Format） CustomEntry 元素，用於 CustomControl for 控制項的 CustomItem 元素（格式為 ExpressionBinding 的 configuration CustomItem 元素）之控制項的 CustomEntry for 控制項（格式） CustomControlName設定之控制項的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="34b24-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="34b24-106">語法</span><span class="sxs-lookup"><span data-stu-id="34b24-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="34b24-107">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="34b24-107">Attributes and Elements</span></span>

<span data-ttu-id="34b24-108">下列各節說明屬性、子專案，以及 `CustomControlName` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="34b24-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="34b24-109">屬性</span><span class="sxs-lookup"><span data-stu-id="34b24-109">Attributes</span></span>

<span data-ttu-id="34b24-110">無。</span><span class="sxs-lookup"><span data-stu-id="34b24-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="34b24-111">子元素</span><span class="sxs-lookup"><span data-stu-id="34b24-111">Child Elements</span></span>

<span data-ttu-id="34b24-112">無。</span><span class="sxs-lookup"><span data-stu-id="34b24-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="34b24-113">父元素</span><span class="sxs-lookup"><span data-stu-id="34b24-113">Parent Elements</span></span>

|<span data-ttu-id="34b24-114">元素</span><span class="sxs-lookup"><span data-stu-id="34b24-114">Element</span></span>|<span data-ttu-id="34b24-115">描述</span><span class="sxs-lookup"><span data-stu-id="34b24-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="34b24-116">設定之控制項的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="34b24-116">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="34b24-117">定義控制項所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="34b24-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="34b24-118">文字值</span><span class="sxs-lookup"><span data-stu-id="34b24-118">Text Value</span></span>

<span data-ttu-id="34b24-119">指定控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="34b24-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="34b24-120">備註</span><span class="sxs-lookup"><span data-stu-id="34b24-120">Remarks</span></span>

<span data-ttu-id="34b24-121">您可以建立可供格式化檔案的所有視圖使用的通用控制項，而且可以建立可供特定視圖使用的 view 控制項。</span><span class="sxs-lookup"><span data-stu-id="34b24-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="34b24-122">下列元素會指定這些控制項的名稱：</span><span class="sxs-lookup"><span data-stu-id="34b24-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="34b24-123">設定之控制項的控制項的名稱元素（格式）</span><span class="sxs-lookup"><span data-stu-id="34b24-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="34b24-124">View 控制項控制項的 Name 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="34b24-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="34b24-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34b24-125">See Also</span></span>

[<span data-ttu-id="34b24-126">設定之控制項的控制項的名稱元素（格式）</span><span class="sxs-lookup"><span data-stu-id="34b24-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="34b24-127">View 控制項控制項的 Name 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="34b24-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="34b24-128">設定之控制項的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="34b24-128">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="34b24-129">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="34b24-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
