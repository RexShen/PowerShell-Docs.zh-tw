---
title: GroupBy (格式) 的 CustomControl 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b8265e872d34ea5dbcedfaa1668d21df8c3b35eb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786062"
---
# <a name="customcontrol-element-for-groupby-format"></a><span data-ttu-id="fa73c-102">GroupBy 的 CustomControl 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fa73c-102">CustomControl Element for GroupBy (Format)</span></span>

<span data-ttu-id="fa73c-103">定義顯示新群組的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="fa73c-103">Defines the custom control that displays the new group.</span></span>

<span data-ttu-id="fa73c-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素（適用于 GroupBy (格式) CustomControl 元素） (</span><span class="sxs-lookup"><span data-stu-id="fa73c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fa73c-105">語法</span><span class="sxs-lookup"><span data-stu-id="fa73c-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
<CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fa73c-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fa73c-106">Attributes and Elements</span></span>

<span data-ttu-id="fa73c-107">下列各節描述元素的屬性、子專案和父項目 `CustomControl` 。</span><span class="sxs-lookup"><span data-stu-id="fa73c-107">The following sections describe the attributes, child elements, and parent element of the `CustomControl` element.</span></span> <span data-ttu-id="fa73c-108">您可以指定任意數目的子項目，並依任何順序列出它們。</span><span class="sxs-lookup"><span data-stu-id="fa73c-108">You can specify any number of child elements and list them in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="fa73c-109">屬性</span><span class="sxs-lookup"><span data-stu-id="fa73c-109">Attributes</span></span>

<span data-ttu-id="fa73c-110">無。</span><span class="sxs-lookup"><span data-stu-id="fa73c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fa73c-111">子元素</span><span class="sxs-lookup"><span data-stu-id="fa73c-111">Child Elements</span></span>

|<span data-ttu-id="fa73c-112">元素</span><span class="sxs-lookup"><span data-stu-id="fa73c-112">Element</span></span>|<span data-ttu-id="fa73c-113">描述</span><span class="sxs-lookup"><span data-stu-id="fa73c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fa73c-114">GroupBy 之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fa73c-114">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="fa73c-115">必要元素。</span><span class="sxs-lookup"><span data-stu-id="fa73c-115">Required element.</span></span><br /><br /> <span data-ttu-id="fa73c-116">提供控制項的定義。</span><span class="sxs-lookup"><span data-stu-id="fa73c-116">Provides the definitions for the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fa73c-117">父項目</span><span class="sxs-lookup"><span data-stu-id="fa73c-117">Parent Elements</span></span>

|<span data-ttu-id="fa73c-118">元素</span><span class="sxs-lookup"><span data-stu-id="fa73c-118">Element</span></span>|<span data-ttu-id="fa73c-119">描述</span><span class="sxs-lookup"><span data-stu-id="fa73c-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fa73c-120">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fa73c-120">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="fa73c-121">定義 Windows PowerShell 如何顯示新的物件群組。</span><span class="sxs-lookup"><span data-stu-id="fa73c-121">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fa73c-122">備註</span><span class="sxs-lookup"><span data-stu-id="fa73c-122">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="fa73c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa73c-123">See Also</span></span>

[<span data-ttu-id="fa73c-124">GroupBy 之 CustomControl 的 CustomEntries 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fa73c-124">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="fa73c-125">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="fa73c-125">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="fa73c-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="fa73c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
