---
title: ViewDefinitions 元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a108c4f8b03e3dec3905181b390aee2c82ab0028
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772479"
---
# <a name="viewdefinitions-element-format"></a>ViewDefinitions 元素 (格式)

定義用來顯示 .NET 物件的視圖。 這些視圖可以使用資料表格式、清單格式、寬格式和自訂控制項格式來顯示物件的屬性和腳本值。

Configuration 元素 (格式) ViewDefinitions (格式 XML) 元素

## <a name="syntax"></a>語法

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述元素的屬性、子專案和父項目 `ViewDefinitions` 。 可以在格式化檔案中定義的視圖數目沒有限制，而且可以依任何順序加入。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[檢視元素 (格式)](./view-element-format.md)|定義用來顯示一個或多個 .NET 物件的視圖。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[設定元素 (格式)](./configuration-element-format.md)|代表格式化檔案的最上層元素。|

## <a name="remarks"></a>備註

如需不同類型之視圖元件的詳細資訊，請參閱下列主題：

- [建立表格檢視](./creating-a-table-view.md)

- [建立清單檢視](./creating-a-list-view.md)

- [建立寬型檢視](./creating-a-wide-view.md)

- [自訂控制項](./creating-custom-controls.md)

## <a name="example"></a>範例

這個範例會顯示一個 `ViewDefinitions` 元素，其中包含資料表視圖和清單視圖的父元素。

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
