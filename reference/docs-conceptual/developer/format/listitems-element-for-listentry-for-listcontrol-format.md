---
title: ListControl 之 ListEntry 的 ListItems 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362737"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>ListControl 之 ListEntry 的 ListItems 元素 (格式)

定義屬性和腳本，其值會顯示在清單視圖的資料列中。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（format） ListEntries 專案（適用于 ListControl 的 ListItems （format） ListControl 元素），其為清單控制項（格式） ListEntry 元素（格式）

## <a name="syntax"></a>語法

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節描述 `ListItems` 專案的屬性、子專案和父項目。 可以指定的子項目數目沒有限制。 子專案的順序會定義在清單視圖中顯示值的順序。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListControl 的專案元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)|必要項目。<br /><br /> 定義清單視圖會顯示其值的屬性或腳本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ListControl 的 ListEntry 元素（格式）](./listentry-element-for-listcontrol-format.md)|提供清單視圖的定義。|

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

[ListControl 的 ListEntry 元素（格式）](./listentry-element-for-listcontrol-format.md)

[ListControl 的專案元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)

[建立清單視圖](./creating-a-list-view.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
