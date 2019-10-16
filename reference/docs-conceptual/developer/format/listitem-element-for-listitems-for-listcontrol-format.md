---
title: 適用于 ListControl 之 ListItems 的專案2元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365127"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>ListControl 之 ListItems 的 ListItem 元素 (格式)

定義屬性或腳本，其值會顯示在清單視圖的資料列中。

ListEntry （格式） ListControl 元素的 ListControl （format） ListItems 元素的設定元素（格式） ViewDefinitions 元素（格式） ListEntries 元素（格式）ListControl 元素的專案（格式）

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

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明 `ListItem` 元素的屬性、子專案和父元素。 只能指定一個屬性或腳本。

### <a name="attributes"></a>屬性

無

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListControl 之專案的格式字串元素（格式）](./formatstring-element-for-listitem-for-listcontrol-format.md)|選擇性元素。<br /><br /> 指定定義屬性或腳本值顯示方式的格式字串。|
|[ListControl 之專案的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|選擇性元素。<br /><br /> 定義必須存在才能使用此清單專案的條件。|
|[ListControl 之專案的標籤元素（格式）](./label-element-for-listitem-for-listcontrol-format.md)|選擇性元素<br /><br /> 指定顯示在資料列中屬性或腳本值左邊的標籤。|
|[ListControl 之專案名稱的 PropertyName 元素（格式）](./propertyname-element-for-listitem-for-listcontrol-format.md)|選擇性元素。<br /><br /> 指定其值顯示在資料列中的 .NET 屬性。|
|[ListControl 之專案的 ScriptBlock 元素（格式）](./scriptblock-element-for-listitem-for-listcontrol-format.md)|選擇性元素。<br /><br /> 指定其值顯示在資料列中的腳本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[清單控制項的 ListItems 元素（格式）](./listitems-element-for-listentry-for-listcontrol-format.md)|定義其值會顯示在清單視圖中的屬性和腳本。|

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

[ListItems 元素（格式）](./listitems-element-for-listentry-for-listcontrol-format.md)

[專案的字串格式元素（格式）](./formatstring-element-for-listitem-for-listcontrol-format.md)

[專案標示的標籤元素（格式）](./label-element-for-listitem-for-listcontrol-format.md)

[專案名稱的 PropertyName 元素（格式）](./propertyname-element-for-listitem-for-listcontrol-format.md)

[專案的 ScriptBlock 元素（格式）](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[建立清單視圖](./creating-a-list-view.md)

[撰寫 Windows PowerShell 格式化和類型檔案](./writing-a-powershell-formatting-file.md)
