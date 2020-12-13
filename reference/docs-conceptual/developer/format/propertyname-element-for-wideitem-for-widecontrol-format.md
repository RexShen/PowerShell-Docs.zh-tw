---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl 之 WideItem 的 PropertyName 元素 (格式)
description: WideControl 之 WideItem 的 PropertyName 元素 (格式)
ms.openlocfilehash: 1d4d5eaf7708dfbd7997122fac156a36487538ea
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665612"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="ed015-103">WideControl 之 WideItem 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="ed015-103">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="ed015-104">指定物件的屬性，其值會顯示在寬視圖中。</span><span class="sxs-lookup"><span data-stu-id="ed015-104">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="ed015-105">設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) WideControl 元素 (格式) WideEntries 元素 (格式) WideEntry 專案 (格式) 之 wideitem 專案 (格式) 之 wideitem (格式的 PropertyName 元素) </span><span class="sxs-lookup"><span data-stu-id="ed015-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ed015-106">語法</span><span class="sxs-lookup"><span data-stu-id="ed015-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ed015-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ed015-107">Attributes and Elements</span></span>

<span data-ttu-id="ed015-108">下列各節描述專案的屬性、子項目和父元素 `PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="ed015-108">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ed015-109">屬性</span><span class="sxs-lookup"><span data-stu-id="ed015-109">Attributes</span></span>

<span data-ttu-id="ed015-110">無。</span><span class="sxs-lookup"><span data-stu-id="ed015-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ed015-111">子元素</span><span class="sxs-lookup"><span data-stu-id="ed015-111">Child Elements</span></span>

<span data-ttu-id="ed015-112">無。</span><span class="sxs-lookup"><span data-stu-id="ed015-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ed015-113">父項目</span><span class="sxs-lookup"><span data-stu-id="ed015-113">Parent Elements</span></span>

|<span data-ttu-id="ed015-114">元素</span><span class="sxs-lookup"><span data-stu-id="ed015-114">Element</span></span>|<span data-ttu-id="ed015-115">描述</span><span class="sxs-lookup"><span data-stu-id="ed015-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ed015-116">之 wideitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="ed015-116">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="ed015-117">定義其值顯示在寬視圖中的屬性或腳本。</span><span class="sxs-lookup"><span data-stu-id="ed015-117">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ed015-118">文字值</span><span class="sxs-lookup"><span data-stu-id="ed015-118">Text Value</span></span>

<span data-ttu-id="ed015-119">指定顯示其值的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="ed015-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="ed015-120">備註</span><span class="sxs-lookup"><span data-stu-id="ed015-120">Remarks</span></span>

<span data-ttu-id="ed015-121">如需有關廣泛視圖元件的詳細資訊，請參閱 [建立廣泛的視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="ed015-121">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ed015-122">範例</span><span class="sxs-lookup"><span data-stu-id="ed015-122">Example</span></span>

<span data-ttu-id="ed015-123">此範例顯示的寬視野，會顯示 ProcessName 屬性的[值。](/dotnet/api/System.Diagnostics.Process)</span><span class="sxs-lookup"><span data-stu-id="ed015-123">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="ed015-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed015-124">See Also</span></span>

[<span data-ttu-id="ed015-125">之 wideitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="ed015-125">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="ed015-126">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="ed015-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ed015-127">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="ed015-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
