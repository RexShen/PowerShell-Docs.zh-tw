---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 ListEntry 的 ListItems 元素 (格式)
description: ListControl 之 ListEntry 的 ListItems 元素 (格式)
ms.openlocfilehash: 1553c81bc559020223a3c1fea10336baf017c9a0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666530"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>ListControl 之 ListEntry 的 ListItems 元素 (格式)

定義屬性和腳本，其值會顯示在清單視圖的資料列中。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListEntries 元素用於清單控制項 (格式) ListControl (格式) ListItems 專案 (格式) 

## <a name="syntax"></a>語法

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `ListItems` 。 可指定的子專案數目沒有任何限制。 子項目的順序會定義值顯示在清單視圖中的順序。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListControl (格式的 [專案] 元素) ](./listitem-element-for-listitems-for-listcontrol-format.md)|必要元素。<br /><br /> 定義清單視圖顯示其值的屬性或腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[ListControl 的 ListEntry 元素 (格式)](./listentry-element-for-listcontrol-format.md)|提供清單視圖的定義。|

## <a name="remarks"></a>備註

如需這種檢視類型的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。

## <a name="example"></a>範例

這個範例會示範定義清單視圖之三個數據列的 XML 元素。

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
