---
title: DisplayError 元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5d46c2fbd48f592db5ba1b33eb6cead8dc1c4698
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774281"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="13073-102">DisplayError 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="13073-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="13073-103">指定在顯示一段資料時發生錯誤時，顯示 #ERR 的字串。</span><span class="sxs-lookup"><span data-stu-id="13073-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="13073-104">Configuration 元素 (格式) DefaultSettings 元素 (格式) DisplayError 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="13073-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="13073-105">語法</span><span class="sxs-lookup"><span data-stu-id="13073-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="13073-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="13073-106">Attributes and Elements</span></span>

<span data-ttu-id="13073-107">下列各節說明屬性、子專案和元素的父元素 `DisplayError` 。</span><span class="sxs-lookup"><span data-stu-id="13073-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="13073-108">屬性</span><span class="sxs-lookup"><span data-stu-id="13073-108">Attributes</span></span>

<span data-ttu-id="13073-109">無。</span><span class="sxs-lookup"><span data-stu-id="13073-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="13073-110">子元素</span><span class="sxs-lookup"><span data-stu-id="13073-110">Child Elements</span></span>

<span data-ttu-id="13073-111">無。</span><span class="sxs-lookup"><span data-stu-id="13073-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="13073-112">父項目</span><span class="sxs-lookup"><span data-stu-id="13073-112">Parent Elements</span></span>

|<span data-ttu-id="13073-113">元素</span><span class="sxs-lookup"><span data-stu-id="13073-113">Element</span></span>|<span data-ttu-id="13073-114">描述</span><span class="sxs-lookup"><span data-stu-id="13073-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="13073-115">DefaultSettings 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="13073-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="13073-116">定義套用至格式化檔案所有視圖的一般設定。</span><span class="sxs-lookup"><span data-stu-id="13073-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="13073-117">備註</span><span class="sxs-lookup"><span data-stu-id="13073-117">Remarks</span></span>

<span data-ttu-id="13073-118">根據預設，當嘗試顯示資料時，如果發生錯誤，資料的位置會保留空白。</span><span class="sxs-lookup"><span data-stu-id="13073-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="13073-119">當此元素設定為 true 時，將會顯示 #ERR 字串。</span><span class="sxs-lookup"><span data-stu-id="13073-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="13073-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13073-120">See Also</span></span>

[<span data-ttu-id="13073-121">DefaultSettings 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="13073-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="13073-122">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="13073-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
