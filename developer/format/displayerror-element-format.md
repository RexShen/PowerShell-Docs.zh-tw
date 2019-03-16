---
title: DisplayError 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056476"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="b75f4-102">DisplayError 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="b75f4-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="b75f4-103">指定顯示一段資料時，發生錯誤時，會顯示 #ERR 的字串。</span><span class="sxs-lookup"><span data-stu-id="b75f4-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="b75f4-104">組態項目 （格式） DefaultSettings 項目 （格式） DisplayError 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="b75f4-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b75f4-105">語法</span><span class="sxs-lookup"><span data-stu-id="b75f4-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b75f4-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="b75f4-106">Attributes and Elements</span></span>

<span data-ttu-id="b75f4-107">下列各節說明屬性、 子項目和父項目`DisplayError`項目。</span><span class="sxs-lookup"><span data-stu-id="b75f4-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b75f4-108">屬性</span><span class="sxs-lookup"><span data-stu-id="b75f4-108">Attributes</span></span>

<span data-ttu-id="b75f4-109">無。</span><span class="sxs-lookup"><span data-stu-id="b75f4-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b75f4-110">子元素</span><span class="sxs-lookup"><span data-stu-id="b75f4-110">Child Elements</span></span>

<span data-ttu-id="b75f4-111">無。</span><span class="sxs-lookup"><span data-stu-id="b75f4-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b75f4-112">父元素</span><span class="sxs-lookup"><span data-stu-id="b75f4-112">Parent Elements</span></span>

|<span data-ttu-id="b75f4-113">元素</span><span class="sxs-lookup"><span data-stu-id="b75f4-113">Element</span></span>|<span data-ttu-id="b75f4-114">描述</span><span class="sxs-lookup"><span data-stu-id="b75f4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b75f4-115">DefaultSettings 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="b75f4-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="b75f4-116">定義套用至的格式化檔案的所有檢視的常見設定。</span><span class="sxs-lookup"><span data-stu-id="b75f4-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b75f4-117">備註</span><span class="sxs-lookup"><span data-stu-id="b75f4-117">Remarks</span></span>

<span data-ttu-id="b75f4-118">根據預設，當發生錯誤時嘗試顯示某份資料，資料的位置會保留空白。</span><span class="sxs-lookup"><span data-stu-id="b75f4-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="b75f4-119">當這個項目設定為 true，#ERR 字串將會顯示。</span><span class="sxs-lookup"><span data-stu-id="b75f4-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="b75f4-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b75f4-120">See Also</span></span>

[<span data-ttu-id="b75f4-121">DefaultSettings 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="b75f4-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="b75f4-122">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="b75f4-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
