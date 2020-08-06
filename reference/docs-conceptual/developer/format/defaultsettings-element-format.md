---
title: DefaultSettings 元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7da7948fc0814e38a8f3910596e223470ec27d75
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787728"
---
# <a name="defaultsettings-element-format"></a>DefaultSettings 元素 (格式)

定義套用至格式化檔案所有視圖的一般設定。 一般設定包括顯示錯誤、在資料表中將文字換行、定義如何擴充集合等等。

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
|[DisplayError 元素 (格式)](./displayerror-element-format.md)|選擇性項目。<br /><br /> 指定在顯示資料時，如果發生錯誤，就會顯示字串 #ERR。|
|[EnumerableExpansions 元素 (格式)](./enumerableexpansions-element-format.md)|選擇性項目。<br /><br /> 定義在視圖中顯示 .NET 物件時，要展開的不同方式。|
|[PropertyCountForTable (格式) ](./propertycountfortable-element-format.md)|選擇性項目。<br /><br /> 指定物件在資料表視圖中顯示物件時必須擁有的最小屬性數目。|
|[ShowError 元素 (格式)](./showerror-element-format.md)|選擇性項目。<br /><br /> 指定顯示資料時，如果發生錯誤，就會顯示完整的錯誤記錄。|
|[WrapTables 元素 (格式)](./wraptables-element-format.md)|選擇性項目。<br /><br /> 指定如果資料表中的資料不符合資料行的寬度，則會將它移到下一行。|

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
