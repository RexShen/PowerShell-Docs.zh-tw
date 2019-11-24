---
title: TableControl 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368197"
---
# <a name="tablecontrol-element-format"></a>TableControl 元素 (格式)

定義視圖的資料表格式。

ViewDefinitions 元素（格式） View 元素（Format） TableControl 元素（格式）

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

下列各節描述 `TableControl` 元素的屬性、子專案和父項目。 您必須指定資料表的資料列。 所有其他子專案都是選擇性的。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|項目|說明|
|-------------|-----------------|
|[TableControl 的 AutoSize 元素（格式）](./autosize-element-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 指定是否根據資料大小來調整資料行大小和資料行數目。|
|[TableControl 的 HideTableHeaders 元素（格式）](./hidetableheaders-element-format.md)|選擇性項目。<br /><br /> 指出是否不顯示資料表的標頭。|
|[TableControl 的 TableHeaders 元素（格式）](./tableheaders-element-format.md)|必要元素。<br /><br /> 定義資料表視圖之資料行的標籤、寬度和對齊方式。|
|[TableControl 的 TableRowEntries 元素（格式）](./tablerowentries-element-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 提供資料表視圖的定義。|

### <a name="parent-elements"></a>父元素

|項目|說明|
|-------------|-----------------|
|[View 元素（格式）](./view-element-format.md)|定義用來顯示一或多個物件成員的視圖。|

## <a name="remarks"></a>備註

如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

這個範例會顯示用來顯示[system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)物件屬性的 `TableControl` 專案。

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

[建立資料表視圖](./creating-a-table-view.md)

[View 元素（格式）](./view-element-format.md)

[TableControl 的 AutoSize 元素（格式）](./autosize-element-for-tablecontrol-format.md)

[HideTableHeaders 元素（格式）](./hidetableheaders-element-format.md)

[TableHeaders 元素（格式）](./tableheaders-element-format.md)

[TableRowEntries 元素（格式）](./tablerowentries-element-for-tablecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
