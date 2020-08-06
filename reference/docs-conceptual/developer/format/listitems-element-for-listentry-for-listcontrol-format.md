---
title: ListControl (格式) 的 ListEntry 的 ListItems 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 03b89a3df2ab0498533d0c00f303f643e0039b25
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781132"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>ListControl 之 ListEntry 的 ListItems 元素 (格式)

定義屬性和腳本，其值會顯示在清單視圖的資料列中。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) ListControl 元素 (format) ListEntry 元素 for ListControl (format) ListItems 元素 for ListControl (Format) 

## <a name="syntax"></a>語法

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述元素的屬性、子專案和父項目 `ListItems` 。 可以指定的子項目數目沒有限制。 子專案的順序會定義在清單視圖中顯示值的順序。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListControl (格式的 [專案] 元素) ](./listitem-element-for-listitems-for-listcontrol-format.md)|必要元素。<br /><br /> 定義清單視圖會顯示其值的屬性或腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[ListControl 的 ListEntry 元素 (格式)](./listentry-element-for-listcontrol-format.md)|提供清單視圖的定義。|

## <a name="remarks"></a>備註

如需這種檢視類型的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。

## <a name="example"></a>範例

這個範例會顯示定義清單視圖之三個數據列的 XML 元素。

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a>另請參閱

[ListControl 的 ListEntry 元素 (格式)](./listentry-element-for-listcontrol-format.md)

[ListControl (格式的 [專案] 元素) ](./listitem-element-for-listitems-for-listcontrol-format.md)

[建立清單檢視](./creating-a-list-view.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
