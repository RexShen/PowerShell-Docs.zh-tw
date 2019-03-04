---
title: ViewDefinitions 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862084"
---
# <a name="viewdefinitions-element-format"></a>ViewDefinitions 元素 (格式)

定義用來顯示.NET 物件的檢視。 這些檢視可以表格格式，清單格式、 寬的格式和自訂控制項格式中顯示的屬性和物件的指令碼值。

組態項目 （格式） ViewDefinitions （格式為 XML） 項目

## <a name="syntax"></a>語法

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`ViewDefinitions`項目。 可以在格式檔案中，定義的檢視數目沒有限制，並將它們加入以任何順序。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[檢視項目 （格式）](./view-element-format.md)|定義用來顯示一或多個.NET 物件的檢視。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[組態項目 （格式）](./configuration-element-format.md)|表示格式化檔案的最上層項目。|

## <a name="remarks"></a>備註

如需有關不同類型的檢視元件的詳細資訊，請參閱下列主題：

- [建立資料表檢視](./creating-a-table-view.md)

- [建立清單檢視](./creating-a-list-view.md)

- [建立寬型檢視](./creating-a-wide-view.md)

- [自訂控制項](./creating-custom-controls.md)

## <a name="example"></a>範例

此範例示範`ViewDefinitions`包含父項目資料表檢視] 和 [清單檢視項目。

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

[組態項目 （格式）](./configuration-element-format.md)

[檢視項目 （格式）](./view-element-format.md)

[建立資料表檢視](./creating-a-table-view.md)

[建立清單檢視](./creating-a-list-view.md)

[建立寬型檢視](./creating-a-wide-view.md)

[自訂控制項](./creating-custom-controls.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
