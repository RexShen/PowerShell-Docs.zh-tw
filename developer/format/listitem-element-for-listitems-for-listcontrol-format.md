---
title: ListItems ListControl （格式） 的 ListItem 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065762"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>ListControl 之 ListItems 的 ListItem 元素 (格式)

定義屬性或其值會顯示 [清單] 檢視的資料列中的指令碼。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries ListControl （格式） ListEntry 元素元素 ListControl （格式） 的 ListControl （格式） ListItems 元素ListItem ListControl 項目 （格式）

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

下列各節說明屬性、 子項目和父項目`ListItem`項目。 可以指定只有一個屬性或指令碼。

### <a name="attributes"></a>屬性

無

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ListControl （格式） 的 ListItem 的 FormatString 元素](./formatstring-element-for-listitem-for-listcontrol-format.md)|選擇性的項目。<br /><br /> 指定的格式字串，定義的屬性或指令碼的值的顯示方式。|
|[ItemSelectionCondition ListControl （格式） 的 ListItem 元素](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|選擇性的項目。<br /><br /> 定義要使用此清單項目必須存在的條件。|
|[ListControl （格式） 的 ListItem label 項目](./label-element-for-listitem-for-listcontrol-format.md)|選擇性的項目<br /><br /> 指定顯示屬性或指令碼中值的資料列左邊的標籤。|
|[PropertyName ListControl （格式） 的 ListItem 元素](./propertyname-element-for-listitem-for-listcontrol-format.md)|選擇性的項目。<br /><br /> 指定其值會顯示資料列中的.NET 屬性。|
|[ScriptBlock ListControl （格式） 的 ListItem 元素](./scriptblock-element-for-listitem-for-listcontrol-format.md)|選擇性的項目。<br /><br /> 指定資料列中顯示其值的指令碼。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[清單控制項 （格式） 的 ListItems 項目](./listitems-element-for-listentry-for-listcontrol-format.md)|定義屬性和其值會顯示在清單檢視中的指令碼。|

## <a name="remarks"></a>備註

清單檢視元件的相關資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。

## <a name="example"></a>範例

這個範例示範定義清單檢視的三個資料列的 XML 項目。 前兩個資料列顯示值的.NET 屬性，以及最後一個資料列會顯示指令碼所產生的值。

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

[ListItems 項目 （格式）](./listitems-element-for-listentry-for-listcontrol-format.md)

[ListItem （格式） 的 FormatString 元素](./formatstring-element-for-listitem-for-listcontrol-format.md)

[ListItem （格式） 的 label 項目](./label-element-for-listitem-for-listcontrol-format.md)

[ListItem （格式） 的屬性名稱項目](./propertyname-element-for-listitem-for-listcontrol-format.md)

[ListItem （格式） 的指令碼區塊項目](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[建立清單檢視](./creating-a-list-view.md)

[撰寫 Windows PowerShell 格式和類型的檔案](./writing-a-powershell-formatting-file.md)
