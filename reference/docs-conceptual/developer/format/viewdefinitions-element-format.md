---
ms.date: 09/13/2016
ms.topic: reference
title: ViewDefinitions 元素 (格式)
description: ViewDefinitions 元素 (格式)
ms.openlocfilehash: fceef0e5ec91e8c59a7b2b90fd31ca422ff0c94d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664573"
---
# <a name="viewdefinitions-element-format"></a>ViewDefinitions 元素 (格式)

定義用來顯示 .NET 物件的視圖。 這些視圖可以用資料表格式、清單格式、寬格式和自訂控制項格式來顯示物件的屬性和腳本值。

Configuration 元素 (格式) ViewDefinitions (格式 XML) 元素

## <a name="syntax"></a>語法

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `ViewDefinitions` 。 在格式化檔案中可定義的視圖數目沒有任何限制，而且可以依任何順序加入。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[檢視元素 (格式)](./view-element-format.md)|定義用來顯示一或多個 .NET 物件的視圖。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[設定元素 (格式)](./configuration-element-format.md)|代表格式化檔案的最上層元素。|

## <a name="remarks"></a>備註

如需不同檢視類型元件的詳細資訊，請參閱下列主題：

- [建立表格檢視](./creating-a-table-view.md)

- [建立清單檢視](./creating-a-list-view.md)

- [建立寬型檢視](./creating-a-wide-view.md)

- [自訂控制項](./creating-custom-controls.md)

## <a name="example"></a>範例

這個範例顯示一個專案 `ViewDefinitions` ，其中包含資料表視圖和清單視圖的父元素。

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a>另請參閱

[設定元素 (格式)](./configuration-element-format.md)

[檢視元素 (格式)](./view-element-format.md)

[建立表格檢視](./creating-a-table-view.md)

[建立清單檢視](./creating-a-list-view.md)

[建立寬型檢視](./creating-a-wide-view.md)

[自訂控制項](./creating-custom-controls.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
