---
title: View 的 CustomControl 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363357"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="4e229-102">檢視的 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="4e229-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="4e229-103">定義視圖的自訂控制項格式。</span><span class="sxs-lookup"><span data-stu-id="4e229-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="4e229-104">Configuration 元素（格式） ViewDefinitions 元素（格式） CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4e229-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4e229-105">語法</span><span class="sxs-lookup"><span data-stu-id="4e229-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4e229-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="4e229-106">Attributes and Elements</span></span>

<span data-ttu-id="4e229-107">下列各節說明屬性、子專案，以及 `CustomControl` 元素的父元素。</span><span class="sxs-lookup"><span data-stu-id="4e229-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="4e229-108">您必須指定一個子項目。</span><span class="sxs-lookup"><span data-stu-id="4e229-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4e229-109">屬性</span><span class="sxs-lookup"><span data-stu-id="4e229-109">Attributes</span></span>

<span data-ttu-id="4e229-110">無。</span><span class="sxs-lookup"><span data-stu-id="4e229-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4e229-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4e229-111">Child Elements</span></span>

|<span data-ttu-id="4e229-112">元素</span><span class="sxs-lookup"><span data-stu-id="4e229-112">Element</span></span>|<span data-ttu-id="4e229-113">描述</span><span class="sxs-lookup"><span data-stu-id="4e229-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4e229-114">CustomControl for View 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4e229-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="4e229-115">必要元素。</span><span class="sxs-lookup"><span data-stu-id="4e229-115">Required element.</span></span><br /><br /> <span data-ttu-id="4e229-116">提供自訂控制項視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="4e229-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4e229-117">父元素</span><span class="sxs-lookup"><span data-stu-id="4e229-117">Parent Elements</span></span>

|<span data-ttu-id="4e229-118">元素</span><span class="sxs-lookup"><span data-stu-id="4e229-118">Element</span></span>|<span data-ttu-id="4e229-119">描述</span><span class="sxs-lookup"><span data-stu-id="4e229-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4e229-120">View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4e229-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="4e229-121">定義用來顯示一個或多個 .NET 物件的視圖。</span><span class="sxs-lookup"><span data-stu-id="4e229-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4e229-122">備註</span><span class="sxs-lookup"><span data-stu-id="4e229-122">Remarks</span></span>

<span data-ttu-id="4e229-123">在大部分情況下，每個控制項視圖只需要一個定義，但是如果您想要使用相同的視圖來顯示不同的 .NET 物件，則可以提供多個定義。</span><span class="sxs-lookup"><span data-stu-id="4e229-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="4e229-124">在這些情況下，您可以為每個物件或一組物件提供個別的定義。</span><span class="sxs-lookup"><span data-stu-id="4e229-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e229-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e229-125">See Also</span></span>

[<span data-ttu-id="4e229-126">CustomControl for View 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4e229-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4e229-127">View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4e229-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="4e229-128">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="4e229-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
