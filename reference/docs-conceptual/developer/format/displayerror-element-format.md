---
title: DisplayError 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363987"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="e23b7-102">DisplayError 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="e23b7-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="e23b7-103">指定在顯示一段資料時發生錯誤時，顯示 #ERR 的字串。</span><span class="sxs-lookup"><span data-stu-id="e23b7-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="e23b7-104">Configuration 元素（格式） DefaultSettings 元素（格式） DisplayError 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e23b7-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e23b7-105">語法</span><span class="sxs-lookup"><span data-stu-id="e23b7-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e23b7-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="e23b7-106">Attributes and Elements</span></span>

<span data-ttu-id="e23b7-107">下列各節說明屬性、子專案，以及 `DisplayError` 專案的父元素。</span><span class="sxs-lookup"><span data-stu-id="e23b7-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e23b7-108">屬性</span><span class="sxs-lookup"><span data-stu-id="e23b7-108">Attributes</span></span>

<span data-ttu-id="e23b7-109">無。</span><span class="sxs-lookup"><span data-stu-id="e23b7-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e23b7-110">子元素</span><span class="sxs-lookup"><span data-stu-id="e23b7-110">Child Elements</span></span>

<span data-ttu-id="e23b7-111">無。</span><span class="sxs-lookup"><span data-stu-id="e23b7-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e23b7-112">父元素</span><span class="sxs-lookup"><span data-stu-id="e23b7-112">Parent Elements</span></span>

|<span data-ttu-id="e23b7-113">元素</span><span class="sxs-lookup"><span data-stu-id="e23b7-113">Element</span></span>|<span data-ttu-id="e23b7-114">描述</span><span class="sxs-lookup"><span data-stu-id="e23b7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e23b7-115">DefaultSettings 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e23b7-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="e23b7-116">定義套用至格式化檔案所有視圖的一般設定。</span><span class="sxs-lookup"><span data-stu-id="e23b7-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e23b7-117">備註</span><span class="sxs-lookup"><span data-stu-id="e23b7-117">Remarks</span></span>

<span data-ttu-id="e23b7-118">根據預設，當嘗試顯示資料時，如果發生錯誤，資料的位置會保留空白。</span><span class="sxs-lookup"><span data-stu-id="e23b7-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="e23b7-119">當此元素設定為 true 時，將會顯示 #ERR 字串。</span><span class="sxs-lookup"><span data-stu-id="e23b7-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="e23b7-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e23b7-120">See Also</span></span>

[<span data-ttu-id="e23b7-121">DefaultSettings 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e23b7-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="e23b7-122">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="e23b7-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
