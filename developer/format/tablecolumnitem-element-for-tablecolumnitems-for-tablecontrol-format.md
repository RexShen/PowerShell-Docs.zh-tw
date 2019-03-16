---
title: TableControl （格式） 的 TableColumnItems TableColumnItem 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 159f943f6bfb33c5403b5714380631351523789f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056986"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>TableControl 之 TableColumnItems 的 TableColumnItem 元素 (格式)

定義屬性或其值會顯示在資料列的資料行的指令碼。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 TableControl （格式） TableRowEntry TableRowEntries TableControl （格式） 的項目TableControl （格式） 的 TableColumnItems TableControl （格式） TableColumnItem 元素 TableControlEntry TableColumnItems 項目

## <a name="syntax"></a>語法

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`TableColumnItem`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl （格式） 的 TableColumnItem 對齊項目](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|選擇性的項目。<br /><br /> 定義資料列的資料行中資料的顯示方式。|
|[TableControl （格式） 的 TableColumnItem 的 FormatString 元素](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|指定用來格式化資料列的資料行中資料的格式模式。|
|[TableControl （格式） 的 TableColumnItem PropertyName 項目](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|選擇性的項目。<br /><br /> 指定其值會顯示屬性的名稱。|
|[TableControl （格式） 的 TableColumnItem 的指令碼區塊項目](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|選擇性的項目。<br /><br /> 指定其值會顯示一個資料列的資料行中的指令碼。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableControl （格式） 的 TableControlEntry TableColumnItems 項目](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|定義屬性或其值會顯示資料列中的指令碼。|

## <a name="remarks"></a>備註

您可以指定屬性的物件或指令碼中的資料列的每個資料行。 如果未不指定任何子項目，項目是預留位置，並會顯示任何資料。

資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。

## <a name="example"></a>範例

此範例示範`TableColumnItem`所顯示的值項目`Status`屬性[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件。

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>另請參閱

[建立資料表檢視](./creating-a-table-view.md)

[TableControl （格式） 的 TableColumnItem 對齊項目](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableColumnItems 項目 （格式）](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl （格式） 的 TableColumnItem 的 FormatString 元素](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableControl （格式） 的 TableColumnItem PropertyName 項目](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableControl （格式） 的 TableColumnItem 的指令碼區塊項目](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
