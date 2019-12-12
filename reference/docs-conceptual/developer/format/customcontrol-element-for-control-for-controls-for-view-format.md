---
title: View （格式）控制項控制項的 CustomControl 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eee505c3-ff2c-4bfb-b48a-037ec34bce72
caps.latest.revision: 8
ms.openlocfilehash: a0c8548dd916a5b32a56462058858f887a9d5803
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363367"
---
# <a name="customcontrol-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="2531a-102">檢視之控制項的控制項 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="2531a-102">CustomControl Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="2531a-103">定義視圖所使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="2531a-103">Defines a control that is used by the view.</span></span>

<span data-ttu-id="2531a-104">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（format） CustomControl 元素 for View 控制項（格式）</span><span class="sxs-lookup"><span data-stu-id="2531a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2531a-105">語法</span><span class="sxs-lookup"><span data-stu-id="2531a-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2531a-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="2531a-106">Attributes and Elements</span></span>

<span data-ttu-id="2531a-107">下列各節說明屬性、子專案，以及 `CustomControl` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="2531a-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="2531a-108">您必須只指定一個子項目。</span><span class="sxs-lookup"><span data-stu-id="2531a-108">You must specify only one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2531a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="2531a-109">Attributes</span></span>

<span data-ttu-id="2531a-110">無。</span><span class="sxs-lookup"><span data-stu-id="2531a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2531a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="2531a-111">Child Elements</span></span>

|<span data-ttu-id="2531a-112">元素</span><span class="sxs-lookup"><span data-stu-id="2531a-112">Element</span></span>|<span data-ttu-id="2531a-113">描述</span><span class="sxs-lookup"><span data-stu-id="2531a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2531a-114">View 之控制項的 CustomControl 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2531a-114">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-view-format.md)|<span data-ttu-id="2531a-115">必要項目。</span><span class="sxs-lookup"><span data-stu-id="2531a-115">Required element.</span></span><br /><br /> <span data-ttu-id="2531a-116">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="2531a-116">Provides the definitions for the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2531a-117">父元素</span><span class="sxs-lookup"><span data-stu-id="2531a-117">Parent Elements</span></span>

|<span data-ttu-id="2531a-118">元素</span><span class="sxs-lookup"><span data-stu-id="2531a-118">Element</span></span>|<span data-ttu-id="2531a-119">描述</span><span class="sxs-lookup"><span data-stu-id="2531a-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2531a-120">View 控制項的控制項元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2531a-120">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="2531a-121">定義可供視圖使用的控制項，以及用來參考控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="2531a-121">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2531a-122">備註</span><span class="sxs-lookup"><span data-stu-id="2531a-122">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="2531a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2531a-123">See Also</span></span>

[<span data-ttu-id="2531a-124">CustomControl for View 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2531a-124">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="2531a-125">View 控制項的控制項元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2531a-125">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="2531a-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="2531a-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
