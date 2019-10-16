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
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a>WideControl 之 WideItem 的 PropertyName 元素 (格式)

指定物件的屬性，其值會顯示在寬視圖中。

之 wideitem 的設定元素（格式） ViewDefinitions 元素（格式） View 元素（格式） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（格式）之 wideitem 元素（格式） PropertyName 元素

## <a name="syntax"></a>語法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明 `PropertyName` 元素的屬性、子專案和父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[之 wideitem 元素（格式）](./wideitem-element-for-widecontrol-format.md)|定義屬性或腳本，其值會顯示在寬視圖中。|

## <a name="text-value"></a>文字值

指定顯示其值的屬性名稱。

## <a name="remarks"></a>備註

如需有關寬視圖元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。

## <a name="example"></a>範例

這個範例顯示的寬視圖，會顯示[system.object](/dotnet/api/System.Diagnostics.Process)物件的 ProcessName 屬性值。

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

## <a name="see-also"></a>另請參閱

[之 wideitem 元素（格式）](./wideitem-element-for-widecontrol-format.md)

[建立寬型視圖](./creating-a-wide-view.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
