---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 TableColumnItem 的 PropertyName 元素 (格式)
description: TableControl 之 TableColumnItem 的 PropertyName 元素 (格式)
ms.openlocfilehash: e83bbdb96d2755013cb9fe065cb98731ba44917f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665578"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a>TableControl 之 TableColumnItem 的 PropertyName 元素 (格式)

指定其值會顯示在資料列的資料行中的屬性。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) TableRowEntries 元素 (格式) TableRowEntry 專案 (格式) TableColumnItems 專案 (格式) 之 tablecolumnitem 專案 (格式) 之 tablecolumnitem (格式的 PropertyName 元素) 

## <a name="syntax"></a>語法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `PropertyName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[之 tablecolumnitem 元素 (格式) ](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|定義其值會顯示在資料列的資料行中的屬性或腳本。|

## <a name="text-value"></a>文字值

指定顯示其值的屬性名稱。

## <a name="remarks"></a>備註

如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

這個範例顯示一個專案，這個專案 `TableColumnItem` 會指定 `Status` [system.object](/dotnet/api/System.Diagnostics.Process) 物件的屬性。

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>另請參閱

[建立表格檢視](./creating-a-table-view.md)

[之 tablecolumnitem 元素 (格式) ](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
