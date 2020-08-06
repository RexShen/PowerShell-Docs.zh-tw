---
title: GroupBy (格式的 ScriptBlock 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e761e02a7910cd598449d564e827889162da9f25
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787677"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="87986-102">GroupBy 的 ScriptBlock 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="87986-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="87986-103">指定每當新群組的值變更時，就會啟動的腳本。</span><span class="sxs-lookup"><span data-stu-id="87986-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="87986-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素用於 GroupBy (格式) ScriptBlock 元素 (</span><span class="sxs-lookup"><span data-stu-id="87986-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="87986-105">語法</span><span class="sxs-lookup"><span data-stu-id="87986-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="87986-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="87986-106">Attributes and Elements</span></span>

<span data-ttu-id="87986-107">下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。</span><span class="sxs-lookup"><span data-stu-id="87986-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="87986-108">屬性</span><span class="sxs-lookup"><span data-stu-id="87986-108">Attributes</span></span>

<span data-ttu-id="87986-109">無。</span><span class="sxs-lookup"><span data-stu-id="87986-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="87986-110">子元素</span><span class="sxs-lookup"><span data-stu-id="87986-110">Child Elements</span></span>

<span data-ttu-id="87986-111">無。</span><span class="sxs-lookup"><span data-stu-id="87986-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="87986-112">父項目</span><span class="sxs-lookup"><span data-stu-id="87986-112">Parent Elements</span></span>

|<span data-ttu-id="87986-113">元素</span><span class="sxs-lookup"><span data-stu-id="87986-113">Element</span></span>|<span data-ttu-id="87986-114">描述</span><span class="sxs-lookup"><span data-stu-id="87986-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87986-115">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="87986-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="87986-116">定義一組 .NET 物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="87986-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="87986-117">文字值</span><span class="sxs-lookup"><span data-stu-id="87986-117">Text Value</span></span>

<span data-ttu-id="87986-118">指定要評估的腳本。</span><span class="sxs-lookup"><span data-stu-id="87986-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="87986-119">備註</span><span class="sxs-lookup"><span data-stu-id="87986-119">Remarks</span></span>

<span data-ttu-id="87986-120">每當此腳本的值變更時，PowerShell 就會啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="87986-120">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="87986-121">當指定此元素時，您無法指定[PropertyName](propertyname-element-for-groupby-format.md)元素來啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="87986-121">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="87986-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87986-122">See Also</span></span>

[<span data-ttu-id="87986-123">GroupBy 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="87986-123">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="87986-124">檢視的 GroupBy 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="87986-124">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="87986-125">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="87986-125">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
