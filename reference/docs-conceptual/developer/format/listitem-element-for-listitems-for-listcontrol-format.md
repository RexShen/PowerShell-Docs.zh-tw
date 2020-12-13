---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 ListItems 的 ListItem 元素 (格式)
description: ListControl 之 ListItems 的 ListItem 元素 (格式)
ms.openlocfilehash: 999491b7851aa4fa21667ad376d7e9853500ca08
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666547"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>ListControl 之 ListItems 的 ListItem 元素 (格式)

定義屬性或腳本，其值會顯示在清單視圖的資料列中。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 元素 (format) ListEntries 元素 for ListControl (format) ListEntry 元素 for ListControl (format) ListItems 專案 (格式) 專案 (格式) 

## <a name="syntax"></a>語法

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `ListItem` 。 只能指定一個屬性或腳本。

### <a name="attributes"></a>屬性

無

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListControl (格式的專案代表的格式格式元素) ](./formatstring-element-for-listitem-for-listcontrol-format.md)|選擇性項目。<br /><br /> 指定定義如何顯示內容或腳本值的格式字串。|
|[ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|選擇性項目。<br /><br /> 定義必須存在才能使用此清單專案的條件。|
|[ListControl 之 ListItem 的標籤元素 (格式)](./label-element-for-listitem-for-listcontrol-format.md)|選擇性元素<br /><br /> 指定在資料列中屬性或腳本值的左邊顯示的標籤。|
|[ListControl 之 ListItem 的 PropertyName 元素 (格式)](./propertyname-element-for-listitem-for-listcontrol-format.md)|選擇性項目。<br /><br /> 指定其值會顯示在資料列中的 .NET 屬性。|
|[ListControl 之 ListItem 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-listitem-for-listcontrol-format.md)|選擇性項目。<br /><br /> 指定其值會顯示在資料列中的腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[清單控制項 (格式的 ListItems 元素) ](./listitems-element-for-listentry-for-listcontrol-format.md)|定義其值顯示在清單視圖中的屬性和腳本。|

## <a name="remarks"></a>備註

如需清單視圖元件的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。

## <a name="example"></a>範例

這個範例會示範定義清單視圖之三個數據列的 XML 元素。 前兩個數據列會顯示 .NET 屬性的值，而最後一個資料列會顯示腳本所產生的值。

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a>另請參閱

[ListItems 元素 (格式) ](./listitems-element-for-listentry-for-listcontrol-format.md)

[專案的格式字串專案 (格式) ](./formatstring-element-for-listitem-for-listcontrol-format.md)

[專案標記的標籤元素 (格式) ](./label-element-for-listitem-for-listcontrol-format.md)

[專案名稱的 PropertyName 元素 (格式) ](./propertyname-element-for-listitem-for-listcontrol-format.md)

[專案專案的 ScriptBlock 元素 (格式) ](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[建立清單檢視](./creating-a-list-view.md)

[寫入 Windows PowerShell 格式和類型檔案](./writing-a-powershell-formatting-file.md)
