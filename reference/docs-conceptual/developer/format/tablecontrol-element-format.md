---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 元素 (格式)
description: TableControl 元素 (格式)
ms.openlocfilehash: 93e05e22d61504d7781b6f3c07f9a3fd0b3c9e8a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651452"
---
# <a name="tablecontrol-element-format"></a>TableControl 元素 (格式)

定義視圖的資料表格式。

ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `TableControl` 。 您必須指定資料表的資料列。 所有其他子項目都是選擇性的。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl 的 AutoSize 元素 (格式)](./autosize-element-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 指定是否根據資料的大小調整資料行大小和資料行數目。|
|[TableControl (格式的 HideTableHeaders 元素) ](./hidetableheaders-element-format.md)|選擇性項目。<br /><br /> 指出是否不顯示資料表的標頭。|
|[TableControl (格式的 TableHeaders 元素) ](./tableheaders-element-format.md)|必要元素。<br /><br /> 定義資料表視圖之資料行的標籤、寬度和對齊方式。|
|[TableControl 的 TableRowEntries 元素 (格式)](./tablerowentries-element-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 提供資料表視圖的定義。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視元素 (格式)](./view-element-format.md)|定義用來顯示一或多個物件成員的視圖。|

## <a name="remarks"></a>備註

如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

此範例顯示 `TableControl` 用來顯示 [system.serviceprocess.dll Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 物件屬性的元素。

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

[建立表格檢視](./creating-a-table-view.md)

[檢視元素 (格式)](./view-element-format.md)

[TableControl 的 AutoSize 元素 (格式)](./autosize-element-for-tablecontrol-format.md)

[HideTableHeaders 元素 (格式)](./hidetableheaders-element-format.md)

[TableHeaders 元素 (格式)](./tableheaders-element-format.md)

[TableRowEntries 元素 (格式) ](./tablerowentries-element-for-tablecontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
