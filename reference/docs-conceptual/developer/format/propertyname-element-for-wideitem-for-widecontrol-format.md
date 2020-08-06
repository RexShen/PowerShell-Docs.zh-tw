---
title: 之 wideitem for WideControl (格式的 PropertyName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7728f960a67faa99eaafb4a4934674e119b8af27
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780469"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="10bd5-102">WideControl 之 WideItem 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="10bd5-102">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="10bd5-103">指定物件的屬性，其值會顯示在寬視圖中。</span><span class="sxs-lookup"><span data-stu-id="10bd5-103">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="10bd5-104">Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 專案 (格式) WideEntries 專案 (格式) WideEntry 專案 (格式) 之 wideitem 元素 (格式) 之 wideitem 的 PropertyName 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="10bd5-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="10bd5-105">語法</span><span class="sxs-lookup"><span data-stu-id="10bd5-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="10bd5-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="10bd5-106">Attributes and Elements</span></span>

<span data-ttu-id="10bd5-107">下列各節描述元素的屬性、子專案和父項目 `PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="10bd5-107">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="10bd5-108">屬性</span><span class="sxs-lookup"><span data-stu-id="10bd5-108">Attributes</span></span>

<span data-ttu-id="10bd5-109">無。</span><span class="sxs-lookup"><span data-stu-id="10bd5-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="10bd5-110">子元素</span><span class="sxs-lookup"><span data-stu-id="10bd5-110">Child Elements</span></span>

<span data-ttu-id="10bd5-111">無。</span><span class="sxs-lookup"><span data-stu-id="10bd5-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="10bd5-112">父項目</span><span class="sxs-lookup"><span data-stu-id="10bd5-112">Parent Elements</span></span>

|<span data-ttu-id="10bd5-113">元素</span><span class="sxs-lookup"><span data-stu-id="10bd5-113">Element</span></span>|<span data-ttu-id="10bd5-114">描述</span><span class="sxs-lookup"><span data-stu-id="10bd5-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="10bd5-115">之 wideitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="10bd5-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="10bd5-116">定義屬性或腳本，其值會顯示在寬視圖中。</span><span class="sxs-lookup"><span data-stu-id="10bd5-116">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="10bd5-117">文字值</span><span class="sxs-lookup"><span data-stu-id="10bd5-117">Text Value</span></span>

<span data-ttu-id="10bd5-118">指定顯示其值的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="10bd5-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="10bd5-119">備註</span><span class="sxs-lookup"><span data-stu-id="10bd5-119">Remarks</span></span>

<span data-ttu-id="10bd5-120">如需有關寬視圖元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="10bd5-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="10bd5-121">範例</span><span class="sxs-lookup"><span data-stu-id="10bd5-121">Example</span></span>

<span data-ttu-id="10bd5-122">這個範例顯示的寬視圖，會顯示[system.object](/dotnet/api/System.Diagnostics.Process)物件的 ProcessName 屬性值。</span><span class="sxs-lookup"><span data-stu-id="10bd5-122">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="10bd5-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10bd5-123">See Also</span></span>

[<span data-ttu-id="10bd5-124">之 wideitem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="10bd5-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="10bd5-125">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="10bd5-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="10bd5-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="10bd5-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
