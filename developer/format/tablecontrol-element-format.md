---
title: TableControl 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: dd48e82452e83f93e2e005c9db53bbc51d8b2eb4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858914"
---
# <a name="tablecontrol-element-format"></a>TableControl 元素 (格式)

定義檢視的資料表格式。

ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式）

## <a name="syntax"></a>語法

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`TableControl`項目。 您必須指定資料表的資料列。 所有其他子項目是選擇性的。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl （格式） 的自動調整項目](./autosize-element-for-tablecontrol-format.md)|選擇性的項目。<br /><br /> 指定是否資料行大小和資料行數目根據調整大小的資料大小。|
|[HideTableHeaders TableControl （格式） 的項目](./hidetableheaders-element-format.md)|選擇性的項目。<br /><br /> 表示是否不會顯示資料表標頭。|
|[TableHeaders TableControl （格式） 的項目](./tableheaders-element-format.md)|必要項目。<br /><br /> 定義標籤、 寬度和資料行的資料表檢視資料的對齊方式。|
|[TableRowEntries TableCotrol （格式） 的項目](./tablerowentries-element-for-tablecontrol-format.md)|選擇性的項目。<br /><br /> 提供 [資料表] 檢視的定義。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[檢視項目 （格式）](./view-element-format.md)|定義的檢視，用來顯示一或多個物件的成員。|

## <a name="remarks"></a>備註

資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。

## <a name="example"></a>範例

此範例示範`TableControl`用來顯示屬性的項目[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件。

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a>另請參閱

[建立資料表檢視](./creating-a-table-view.md)

[檢視項目 （格式）](./view-element-format.md)

[TableControl （格式） 的自動調整項目](./autosize-element-for-tablecontrol-format.md)

[HideTableHeaders 項目 （格式）](./hidetableheaders-element-format.md)

[TableHeaders 項目 （格式）](./tableheaders-element-format.md)

[TableRowEntries 項目 （格式）](./tablerowentries-element-for-tablecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
