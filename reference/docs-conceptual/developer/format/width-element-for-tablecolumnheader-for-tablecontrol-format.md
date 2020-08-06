---
title: TableControl (格式的之 tablecolumnheader 寬度元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e9540d3d351041ad7cb98a21bb360ebea7eca117
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779908"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>TableControl 之 TableColumnHeader 的寬度元素 (格式)

定義資料行之字元) 的寬度 (。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 專案 (格式) TableControl (格式) 之 tablecolumnheader 元素 TableHeaders 針對 TableControl (format) Width 元素之 tablecolumnheader (格式) 

## <a name="syntax"></a>語法

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明定義資料行標頭時所使用之元素的屬性、子專案和父項目 `Width` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[TableControl (格式的 TableHeaders 的之 tablecolumnheader 元素) ](./tablecolumnheader-element-format.md)|定義資料表資料行的標籤、寬度和對齊方式。|

## <a name="text-value"></a>文字值

可能的話，請指定寬度 (字元) 大於顯示內容值的長度。

## <a name="remarks"></a>備註

如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例顯示 `TableColumnHeader` 其寬度為16個字元的元素。

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>另請參閱

[建立表格檢視](./creating-a-table-view.md)

[TableControl (格式的 TableHeader 的之 tablecolumnheader 元素) ](./tablecolumnheader-element-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
