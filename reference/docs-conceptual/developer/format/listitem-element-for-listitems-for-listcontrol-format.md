---
title: 適用于 ListControl (格式的 ListItems 的 [專案] 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e72a887e8bd1f93bacb663e3079eeaec34bdfa51
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785671"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>ListControl 之 ListItems 的 ListItem 元素 (格式)

定義屬性或腳本，其值會顯示在清單視圖的資料列中。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListControl (格式) ListEntry 元素，ListControl (格式) ListItems 元素 (格式) 

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

下列各節描述元素的屬性、子專案和父項目 `ListItem` 。 只能指定一個屬性或腳本。

### <a name="attributes"></a>屬性

無

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[適用于 ListControl (格式之專案的格式字串元素) ](./formatstring-element-for-listitem-for-listcontrol-format.md)|選擇性項目。<br /><br /> 指定定義屬性或腳本值顯示方式的格式字串。|
|[ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|選擇性項目。<br /><br /> 定義必須存在才能使用此清單專案的條件。|
|[ListControl 之 ListItem 的標籤元素 (格式)](./label-element-for-listitem-for-listcontrol-format.md)|選擇性元素<br /><br /> 指定顯示在資料列中屬性或腳本值左邊的標籤。|
|[ListControl 之 ListItem 的 PropertyName 元素 (格式)](./propertyname-element-for-listitem-for-listcontrol-format.md)|選擇性項目。<br /><br /> 指定其值顯示在資料列中的 .NET 屬性。|
|[ListControl 之 ListItem 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-listitem-for-listcontrol-format.md)|選擇性項目。<br /><br /> 指定其值顯示在資料列中的腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[清單控制項 (格式的 ListItems 元素) ](./listitems-element-for-listentry-for-listcontrol-format.md)|定義其值會顯示在清單視圖中的屬性和腳本。|

## <a name="remarks"></a>備註

如需清單視圖之元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。

## <a name="example"></a>範例

這個範例會顯示定義清單視圖之三個數據列的 XML 元素。 前兩個數據列會顯示 .NET 屬性的值，而最後一個資料列則會顯示腳本所產生的值。

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

[專案的格式字串元素 (格式) ](./formatstring-element-for-listitem-for-listcontrol-format.md)

[專案的標籤元素 (格式) ](./label-element-for-listitem-for-listcontrol-format.md)

[專案名稱的 PropertyName 元素 (格式) ](./propertyname-element-for-listitem-for-listcontrol-format.md)

[專案的 ScriptBlock 元素 (格式) ](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[建立清單檢視](./creating-a-list-view.md)

[撰寫 Windows PowerShell 格式化和類型檔案](./writing-a-powershell-formatting-file.md)
