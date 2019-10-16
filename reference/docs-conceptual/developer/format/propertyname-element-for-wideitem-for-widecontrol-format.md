---
title: WideControl 之之 wideitem 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364937"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="86254-102">WideControl 之 WideItem 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="86254-102">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="86254-103">指定物件的屬性，其值會顯示在寬視圖中。</span><span class="sxs-lookup"><span data-stu-id="86254-103">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="86254-104">之 wideitem 的設定元素（格式） ViewDefinitions 元素（格式） View 元素（格式） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（格式）之 wideitem 元素（格式） PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="86254-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="86254-105">語法</span><span class="sxs-lookup"><span data-stu-id="86254-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="86254-106">屬性與元素</span><span class="sxs-lookup"><span data-stu-id="86254-106">Attributes and Elements</span></span>

<span data-ttu-id="86254-107">下列各節說明 `PropertyName` 元素的屬性、子專案和父元素。</span><span class="sxs-lookup"><span data-stu-id="86254-107">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="86254-108">屬性</span><span class="sxs-lookup"><span data-stu-id="86254-108">Attributes</span></span>

<span data-ttu-id="86254-109">無。</span><span class="sxs-lookup"><span data-stu-id="86254-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="86254-110">子元素</span><span class="sxs-lookup"><span data-stu-id="86254-110">Child Elements</span></span>

<span data-ttu-id="86254-111">無。</span><span class="sxs-lookup"><span data-stu-id="86254-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="86254-112">父元素</span><span class="sxs-lookup"><span data-stu-id="86254-112">Parent Elements</span></span>

|<span data-ttu-id="86254-113">元素</span><span class="sxs-lookup"><span data-stu-id="86254-113">Element</span></span>|<span data-ttu-id="86254-114">描述</span><span class="sxs-lookup"><span data-stu-id="86254-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86254-115">之 wideitem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="86254-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="86254-116">定義屬性或腳本，其值會顯示在寬視圖中。</span><span class="sxs-lookup"><span data-stu-id="86254-116">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="86254-117">文字值</span><span class="sxs-lookup"><span data-stu-id="86254-117">Text Value</span></span>

<span data-ttu-id="86254-118">指定顯示其值的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="86254-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="86254-119">備註</span><span class="sxs-lookup"><span data-stu-id="86254-119">Remarks</span></span>

<span data-ttu-id="86254-120">如需有關寬視圖元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="86254-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="86254-121">範例</span><span class="sxs-lookup"><span data-stu-id="86254-121">Example</span></span>

<span data-ttu-id="86254-122">這個範例顯示的寬視圖，會顯示[system.object](/dotnet/api/System.Diagnostics.Process)物件的 ProcessName 屬性值。</span><span class="sxs-lookup"><span data-stu-id="86254-122">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="86254-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86254-123">See Also</span></span>

[<span data-ttu-id="86254-124">之 wideitem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="86254-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="86254-125">建立寬型視圖</span><span class="sxs-lookup"><span data-stu-id="86254-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="86254-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="86254-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
