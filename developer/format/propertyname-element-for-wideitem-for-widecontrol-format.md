---
title: PropertyName WideItem 如 WideControl （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064640"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="27abf-102">WideControl 之 WideItem 的 PropertyName 元素 (格式)</span><span class="sxs-lookup"><span data-stu-id="27abf-102">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="27abf-103">指定其值會顯示在寬型檢視物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="27abf-103">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="27abf-104">組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry 項目 （格式） WideItem 項目 （格式） PropertyName 項目 WideItem （格式）</span><span class="sxs-lookup"><span data-stu-id="27abf-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="27abf-105">語法</span><span class="sxs-lookup"><span data-stu-id="27abf-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="27abf-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="27abf-106">Attributes and Elements</span></span>

<span data-ttu-id="27abf-107">下列各節說明屬性、 子項目和父項目`PropertyName`項目。</span><span class="sxs-lookup"><span data-stu-id="27abf-107">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="27abf-108">屬性</span><span class="sxs-lookup"><span data-stu-id="27abf-108">Attributes</span></span>

<span data-ttu-id="27abf-109">無。</span><span class="sxs-lookup"><span data-stu-id="27abf-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="27abf-110">子元素</span><span class="sxs-lookup"><span data-stu-id="27abf-110">Child Elements</span></span>

<span data-ttu-id="27abf-111">無。</span><span class="sxs-lookup"><span data-stu-id="27abf-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="27abf-112">父項目</span><span class="sxs-lookup"><span data-stu-id="27abf-112">Parent Elements</span></span>

|<span data-ttu-id="27abf-113">項目</span><span class="sxs-lookup"><span data-stu-id="27abf-113">Element</span></span>|<span data-ttu-id="27abf-114">描述</span><span class="sxs-lookup"><span data-stu-id="27abf-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="27abf-115">WideItem 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="27abf-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="27abf-116">定義屬性或其值會顯示在寬型檢視的指令碼。</span><span class="sxs-lookup"><span data-stu-id="27abf-116">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="27abf-117">文字值</span><span class="sxs-lookup"><span data-stu-id="27abf-117">Text Value</span></span>

<span data-ttu-id="27abf-118">指定其值會顯示屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="27abf-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="27abf-119">備註</span><span class="sxs-lookup"><span data-stu-id="27abf-119">Remarks</span></span>

<span data-ttu-id="27abf-120">如需詳細的寬型檢視元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="27abf-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="27abf-121">範例</span><span class="sxs-lookup"><span data-stu-id="27abf-121">Example</span></span>

<span data-ttu-id="27abf-122">此範例示範顯示之 ProcessName 屬性的值的寬型檢視[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件。</span><span class="sxs-lookup"><span data-stu-id="27abf-122">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="27abf-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27abf-123">See Also</span></span>

[<span data-ttu-id="27abf-124">WideItem 項目 （格式）</span><span class="sxs-lookup"><span data-stu-id="27abf-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="27abf-125">建立寬型檢視</span><span class="sxs-lookup"><span data-stu-id="27abf-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="27abf-126">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="27abf-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
