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
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a>WideControl 之 WideItem 的 PropertyName 元素 (格式)

指定物件的屬性，其值會顯示在寬視圖中。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 專案 (格式) WideEntries 專案 (格式) WideEntry 專案 (格式) 之 wideitem 元素 (格式) 之 wideitem 的 PropertyName 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述元素的屬性、子專案和父項目 `PropertyName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[之 wideitem 元素 (格式) ](./wideitem-element-for-widecontrol-format.md)|定義屬性或腳本，其值會顯示在寬視圖中。|

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

[之 wideitem 元素 (格式) ](./wideitem-element-for-widecontrol-format.md)

[建立寬型檢視](./creating-a-wide-view.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
