---
ms.date: 09/13/2016
ms.topic: reference
title: DefaultSettings 元素 (格式)
description: DefaultSettings 元素 (格式)
ms.openlocfilehash: 1c2055b38a416fe2d75fa20c6c87e92d9eed4285
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666717"
---
# <a name="defaultsettings-element-format"></a>DefaultSettings 元素 (格式)

定義適用于格式檔案所有視圖的一般設定。 一般設定包括顯示錯誤、在資料表中包裝文字、定義集合的擴充方式等等。

Configuration 元素 (格式) DefaultSettings 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `DefaultSettings` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[DisplayError 元素 (格式)](./displayerror-element-format.md)|選擇性項目。<br /><br /> 指定當顯示資料時，出現錯誤時，會顯示字串 #ERR。|
|[EnumerableExpansions 元素 (格式)](./enumerableexpansions-element-format.md)|選擇性項目。<br /><br /> 定義在顯示于視圖時，.NET 物件展開的不同方式。|
|[PropertyCountForTable (格式) ](./propertycountfortable-element-format.md)|選擇性項目。<br /><br /> 指定物件在資料表視圖中顯示物件時必須擁有的最小屬性數目。|
|[ShowError 元素 (格式)](./showerror-element-format.md)|選擇性項目。<br /><br /> 指定當顯示資料時，發生錯誤時，就會顯示完整的錯誤記錄。|
|[WrapTables 元素 (格式)](./wraptables-element-format.md)|選擇性項目。<br /><br /> 指定當資料表中的資料不符合資料行的寬度時，會將資料表中的資料移到下一行。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[組態元素](./configuration-element-format.md)|代表格式化檔案的最上層元素。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[組態元素](./configuration-element-format.md)

[DisplayError 元素 (格式)](./displayerror-element-format.md)

[EnumerableExpansions 元素 (格式)](./enumerableexpansions-element-format.md)

[PropertyCountForTable (格式) ](./propertycountfortable-element-format.md)

[ShowError 元素 (格式)](./showerror-element-format.md)

[WrapTables 元素 (格式)](./wraptables-element-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
