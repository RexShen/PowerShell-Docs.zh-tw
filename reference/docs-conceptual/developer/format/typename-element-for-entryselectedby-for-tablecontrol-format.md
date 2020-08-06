---
title: 之 entryselectedby for TableControl (格式的 TypeName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c514d3e6155278ddd3a0565c87e9377dc8419356
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780197"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a>TableControl 之 EntrySelectedBy 的 TypeName 元素 (格式)

指定使用此資料表視圖專案的 .NET 類型。 可以針對資料表專案指定的類型數目沒有限制。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 專案 (格式) TableRowEntries 專案 (格式) TableRowEntry 專案 (格式) 之 entryselectedby 元素 (格式) 之 entryselectedby 的 TypeName 元素 TableRowEntry (格式) 

## <a name="syntax"></a>語法

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `TypeName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[之 entryselectedby 元素 (格式) ](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|定義使用此專案的 .NET 類型，或必須存在才能使用此專案的條件。|

## <a name="text-value"></a>文字值

指定 .NET 類型的名稱。

## <a name="remarks"></a>備註

每個清單專案都必須定義至少一個型別名稱、選擇集或選取條件。

如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。

## <a name="see-also"></a>另請參閱

[建立表格檢視](./creating-a-table-view.md)

[之 entryselectedby 元素 (格式) ](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
