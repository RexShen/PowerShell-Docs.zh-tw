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
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a>WideControl 之 WideItem 的 PropertyName 元素 (格式)

指定物件的屬性，其值會顯示在寬視圖中。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) WideControl 元素 (格式) WideEntries 元素 (格式) WideEntry 專案 (格式) 之 wideitem 專案 (格式) 之 wideitem (格式的 PropertyName 元素) 

## <a name="syntax"></a>語法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `PropertyName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[之 wideitem 元素 (格式) ](./wideitem-element-for-widecontrol-format.md)|定義其值顯示在寬視圖中的屬性或腳本。|

## <a name="text-value"></a>文字值

指定顯示其值的屬性名稱。

## <a name="remarks"></a>備註

如需有關廣泛視圖元件的詳細資訊，請參閱 [建立廣泛的視圖](./creating-a-wide-view.md)。

## <a name="example"></a>範例

此範例顯示的寬視野，會顯示 ProcessName 屬性的[值。](/dotnet/api/System.Diagnostics.Process)

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

[之 wideitem 元素 (格式) ](./wideitem-element-for-widecontrol-format.md)

[建立寬型檢視](./creating-a-wide-view.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
